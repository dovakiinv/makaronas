# Context Map: AI Call Assembly Pipeline

*Where each piece of AI context comes from and how it reaches the model.*

This is a debugging document. When someone asks "why did the Trickster say that?", start here.

---

## The 8-Layer System Prompt

The system prompt is assembled by `ContextManager` (`backend/ai/context.py`). Each layer is a string block; non-None layers are joined with `\n\n`.

| Layer | Source | Content | When absent |
|-------|--------|---------|-------------|
| **1. Persona** | `prompts/tasks/{task_id}/persona.md` or `prompts/default/persona.md` | Trickster character definition, voice, attitude | Layer skipped (no persona instruction) |
| **2. Behaviour** | `prompts/tasks/{task_id}/behaviour.md` or `prompts/default/behaviour.md` | Dialogue strategy, exchange pacing, how to push back | Layer skipped |
| **3. Safety** | `prompts/tasks/{task_id}/safety.md` or `prompts/default/safety.md` | Hard safety boundaries for prompt-level enforcement | Layer skipped |
| **4. Task override** | `prompts/tasks/{task_id}/{provider}.md` (optional) | Provider-specific tuning (e.g., Gemini-specific phrasing) | Layer skipped (uses base prompts only) |
| **5. Task context** | Cartridge data: `ai_config.persona_mode`, `session.current_phase`, `evaluation.patterns_embedded`, `evaluation.checklist`, `evaluation.pass_conditions` | What the Trickster is trying to do in this task — patterns to embed, evaluation criteria, pass/fail conditions | Minimal header only |
| **6. Safety config** | Cartridge: `safety.content_boundaries`, `safety.intensity_ceiling` | Runtime safety parameters (topic boundaries, intensity cap) | Always present (cartridge validation enforces safety block) |
| **7. Language** | Hard-coded in `_build_language_instruction()` | "Always respond in Lithuanian" — never omitted | Always present |
| **8. Student path** | `session.choices[].context_label` | What the student chose in prior static phases (e.g., "Student selected 'Share without reading'") | Layer skipped if no choices have context_label |

**Bonus: Redaction context** — Appended after layer 8 when `session.last_redaction_reason` is set. Tells the Trickster its previous response was redacted and to stay in character. One-shot: cleared after injection.

### Debrief differences

The debrief call (`assemble_debrief_call`) uses the same layers 1-4, but replaces layer 5:

- **Dialogue layer 5:** Evaluation criteria framed as "what to do" (adversarial stance)
- **Debrief layer 5:** Same data framed as "what to reveal" + explicit instruction to drop the adversarial stance, connect techniques to the student's actual statements, and explain the lesson

Debrief includes full exchange history (no trimming) and no transition tool.

---

## Prompt Resolution: Snapshots vs Loader

On the **first AI call** for a task attempt, prompts are loaded from disk and snapshotted into `session.prompt_snapshots`. All subsequent calls for that session use the snapshot.

This guarantees **live session integrity** (P21): if a teacher edits prompt files mid-session, in-progress students keep their original prompts. No mid-conversation personality shifts.

Resolution order: `session.prompt_snapshots` -> `PromptLoader.load_trickster_prompts(provider, task_id)`.

The PromptLoader itself resolves: task-specific file -> default file -> None (layer skipped).

---

## Messages (Exchange History)

Exchange history is formatted by `_format_exchanges()`:
- `Exchange(role="student")` -> `{"role": "user", "content": "..."}`
- `Exchange(role="trickster")` -> `{"role": "assistant", "content": "..."}`

Messages are chronological. For dialogue calls, the `ContextManager` trims oldest exchange *pairs* (user + assistant together) if the total estimated tokens exceed the budget (default 100K). Lithuanian text uses ~3 chars/token heuristic.

The system prompt is **never** trimmed.

---

## Transition Tool

The `transition_phase` tool is included in `AssembledContext.tools` only when `exchange_count >= min_exchanges` (from `FreeformInteraction`). This prevents premature transitions.

Tool signals: `"understood"` (student gets it), `"partial"` (partial understanding), `"max_reached"` (timeout after max exchanges).

The TricksterEngine maps these signals to cartridge-defined `ai_transitions`: `on_success`, `on_partial`, `on_max_exchanges`. The cartridge is always the source of truth for the state machine.

---

## Token Budget

Default: 100,000 tokens. Estimation uses `len(text) / 3` (Lithuanian ~3 chars/token).

Budget priority:
1. System prompt (never trimmed)
2. Recent exchanges (trimmed from oldest pair)
3. Tool definition (minimal footprint)

---

## SSE Response Pipeline

After the AI call is assembled and sent to the provider:

```
TricksterEngine.respond()
  -> AIProvider.stream()             # Returns AsyncIterator[str] (raw tokens)
  -> Engine accumulates, checks safety, resolves transitions
  -> Returns TricksterResult (token_iterator + post-completion fields)

student.py _stream_trickster_response()
  -> Yields format_sse_event("token", TokenEvent)    # Per-token
  -> After exhaustion, reads result.redaction_data / result.done_data
  -> Yields format_sse_event("redact", RedactEvent)   # If safety violation
  -> OR yields format_sse_event("done", DoneEvent)     # If clean
  -> Logs usage via log_ai_call()
  -> Saves session via session_store.save_session()

create_sse_response()
  -> Wraps generator in StreamingResponse (text/event-stream)
```

**DoneEvent data shapes:**

Dialogue: `{"phase_transition": str|null, "next_phase": str|null, "exchanges_count": int}`

Debrief: `{"debrief_complete": true}`

---

## Adding Context Layers

When future visions add `learning_profile` or `full_history` context levels:

1. Add a new `_build_*` method to `ContextManager`
2. Call it from `_build_dialogue_system_prompt()` at the appropriate position
3. The `context_requirements` field on `AiConfig` already supports arbitrary strings — resolve them in `assemble_trickster_call()` where the MVP stub currently logs and falls through to `session_only`
4. Update this document

# Makaronas

*Teaching resilience against information manipulation through adversarial AI.*

## The Spirit

This platform teaches teenagers to deeply understand how false narratives are manufactured, who benefits, and why they spread. AI is the teacher, not the examiner — it engages, challenges, and guides students through lived adversarial experience. Evaluation is a byproduct of that teaching, not its purpose.

When in doubt, read `FRAMEWORK.md`. It's the lens for every decision.

---

## Architectural Patterns

### Tier Discipline

Modules are organized into dependency tiers. Lower tiers NEVER import higher tiers.

- **Tier 1 (leaf):** `backend/tasks/schemas.py`, `backend/schemas.py` — Pydantic models, stdlib only. No disk I/O, no framework imports.
- **Tier 2 (services):** `backend/tasks/loader.py`, `backend/tasks/registry.py` — business logic, may import Tier 1.
- **Tier 3 (orchestration):** API routes, app setup — imports anything below.

This matters because V6 (evaluation) imports task schemas. If schemas import loader code, you get circular dependencies.

### PresentationBlock vs ContentBlock

Two different concepts in two different modules:

- **`ContentBlock`** (`backend/schemas.py`) — Runtime provenance marker. Says whether content came from AI or static source. Has `source: Literal["ai", "static"]`.
- **`PresentationBlock`** (`backend/tasks/schemas.py`) — Authoring structure. What the student sees in a task cartridge. Has `type`, `id`, `data`.

Never confuse these. Different names, different modules, different purposes.

### Open Type Pattern

Content block types and interaction types are open sets, not closed enums. This is how the format stays extensible without schema migrations.

**The pattern:** Every block/interaction carries a `type` string and a `data`/`config` dict. Known types get full Pydantic validation. Unknown types route to a `GenericBlock(type: str, data: dict)` fallback.

**Critical implementation detail:** Pydantic v2 discriminated unions are strict — unknown `type` values throw `ValidationError`. You MUST use `model_validator(mode='before')` to check the type string and route unknown types to the generic fallback. Without this, adding a new block type requires a code change, killing the extensibility story.

### Taxonomy Validation via Context Injection

Trigger and technique values are validated against `content/taxonomy.json`, but `tasks/schemas.py` must stay Tier 1 (no disk I/O).

**The pattern:** `loader.py` reads `taxonomy.json` once at startup, then passes it into every `model_validate(json_data, context={'taxonomy': known_taxonomies})` call. Model validators access taxonomy through `info.context['taxonomy']`. This keeps schemas pure and testable in isolation (tests inject their own taxonomy context).

### Path = Identity

`task_id` in the cartridge JSON must exactly match its parent directory name. `content/tasks/task-02/task.json` containing `"task_id": "task-01"` is a **hard load error**. This prevents silent corruption in student profiles and prerequisite chains.

### Frozen Models

Loaded cartridges are immutable (`ConfigDict(frozen=True)`). Task data is reference content, not mutable state.

### Facts from Data, Personalization from AI

When ground truth exists as structured data (pattern counts, evaluation results, task metadata), the platform renders it programmatically. AI personalizes *around* the facts but never *generates* them. The Trickster says "I used 3 patterns" because the platform counted `patterns_embedded`; the AI adds "and you caught two of them" based on the student's responses.

In a platform that teaches students to distrust misinformation, the AI must not hallucinate facts about its own behaviour.

---

## Task Cartridge Patterns

### The Three Task Types

- **`ai_driven`** — AI engages the student in real-time adversarial dialogue. The teaching mode. Expensive.
- **`static`** — Deterministic button choices. Zero AI cost. Learning comes from the choice itself.
- **`hybrid`** — Static phases set context, AI phases deepen the teaching. Most common type.

The litmus test: does the student need to be challenged, guided, and pushed back on in real-time? If yes, AI. If not, static.

### Clean Tasks (`is_clean`)

Tasks with NO manipulation — the student must recognize legitimate content. Evaluation inverts: "Trickster wins" means the student falsely accused clean content.

- `is_clean` is an **explicit boolean flag**, not derived from empty `patterns_embedded`.
- `is_clean: true` + non-empty `patterns_embedded` = **hard load error** (contradiction).
- `is_clean: false` + empty `patterns_embedded` = **warning** (may be a draft in progress).

### AI Phase Transitions

For static phases, transitions live on buttons. For AI phases, the Trickster engine decides *when* the conversation ends — but the **cartridge** decides *where* the flow goes.

AI phases declare `ai_transitions` mapping engine signals to target phases:
- `on_success` → reveal phase for "Trickster loses"
- `on_max_exchanges` → reveal phase for timeout
- `on_partial` → reveal phase for partial understanding

The engine emits a signal; the cartridge maps it to the next phase. The cartridge is always the single source of truth for the state machine.

### Static-to-AI Context Labels

In hybrid tasks, button choices carry a `context_label` (e.g., `"Student selected 'Share without reading'"`) that gets recorded to session exchange history. This ensures AI phases inherit the full static path context — the Trickster knows what the student chose without guessing.

---

## Coding Standards

### Model ID Discipline — Three-Layer Abstraction

`models.py` is the **single source of truth** for all model configuration. It contains two mappings:

**Layer 1 → 2: Capability tiers → model families.** Task cartridges declare a capability tier (`"fast"`, `"standard"`, `"complex"`), not a model name. Content authors think about what intelligence the task needs, not which provider serves it.

**Layer 2 → 3: Model families → model IDs.** Family constants (`CLAUDE_HAIKU`, `GEMINI_FLASH_LITE`) map to specific versioned IDs (`"claude-haiku-4-5-20251001"`).

```python
# models.py (single source of truth)

from dataclasses import dataclass

# Layer 3: Model IDs (change when provider releases new version)
CLAUDE_HAIKU = "claude-haiku-4-5-20251001"
CLAUDE_SONNET = "claude-sonnet-4-6"
GEMINI_FLASH_LITE = "gemini-flash-lite-latest"
GEMINI_FLASH = "gemini-3-flash-preview"
GEMINI_PRO = "gemini-3.1-pro-preview"

@dataclass(frozen=True)
class ModelConfig:
    provider: str          # "gemini" or "anthropic"
    model_id: str
    thinking_budget: int = 0  # Gemini thinking tokens (0 = off)

# Layer 2: Capability tiers (team experiments here)
# MVP: Gemini-first for speed and cost
TIER_MAP: dict[str, ModelConfig] = {
    "fast": ModelConfig(provider="gemini", model_id=GEMINI_FLASH_LITE),
    "standard": ModelConfig(provider="gemini", model_id=GEMINI_FLASH),
    "complex": ModelConfig(provider="gemini", model_id=GEMINI_PRO),
}
```

**Who changes what:**
- **Content authors** pick a tier in the cartridge (`"model_preference": "standard"`). Never touch `models.py`.
- **Team** swaps model families by changing tier mappings. Zero cartridge edits. 50 tasks instantly use the new model.
- **Model upgrades** change the ID constants. Tier mappings and cartridges untouched.

Nowhere in the codebase outside `models.py` should a raw model ID (e.g., `"claude-sonnet-4-6"`) appear. No exceptions.

### Python Style

- **Google-style docstrings** — summary in imperative mood ("Extracts..." not "Extract...")
- **Type hints in signatures**, not docstrings — `-> None` for no return value
- **`from typing import List, Dict, Optional, Any`** as needed
- **No tuples in persisted data** — JSON roundtrip converts to lists
- **Dates as ISO-8601 strings** in JSON
- **Pydantic models need clean JSON round-trip**

### Import Discipline

- Organize modules into dependency tiers (see above)
- Lower tiers NEVER import higher tiers
- Prefer keeping related code in one file over splitting into circular imports

---

## Language

Lithuanian is the exclusive language for all content, UI, and AI interactions. All task cartridges, prompts, Trickster dialogue, and student-facing text are in Lithuanian. The architecture leaves the door open structurally for future localization (locale fields on cartridges), but no effort is spent on multi-language support until V12.

---

## Key Files

- `FRAMEWORK.md` — 20 engineering principles. The lens for every decision.
- `PLATFORM_VISION.md` — Master spec. The 12 visions, build order, design principles.
- `backend/schemas.py` — Core Pydantic models (GameSession, StudentProfile, Exchange, ContentBlock).
- `backend/tasks/` — V2's domain: schemas, loader, registry.
- `AUTH.md` — Identity roadmap. MVP anonymous sessions, future persistent identity, touchpoints.
- `content/tasks/{task_id}/task.json` — Cartridge files.
- `content/taxonomy.json` — Known triggers, techniques, mediums. Warn-don't-block validation. Tags excluded (freeform).
- `prompts/tasks/{task_id}/` — Prompt files (task.md base, model-specific overrides).
- `backend/models.py` — Model IDs and capability tier mappings. Single source of truth for all model configuration.

---

## Deployment

**GitHub remote:** `https://github.com/DID-org/makaronas.git` — the repo lives under the **DID-org** organization, not Vinga's personal account. Her personal handle is `dovahkiin-v` (renamed from an older one without the hyphen), but `makaronas` is under DID-org. If `git push` fails with "repository not found," check the remote URL first — a stale remote pointing at her personal account is the usual cause.

The team testing instance is deployed on **Railway** via CLI. No GitHub integration — deploy manually from the project directory.

```bash
# From /home/vinga/projects/makaronas:
railway up
```

**Remind Vinga to run `railway up` after committing changes that the team should see.** Commits to main do NOT auto-deploy — manual push required.

Environment variable `GOOGLE_API_KEY` is set on Railway's side (Variables tab in dashboard).

**Server restart gotcha:** The `--reload` flag watches Python files but NOT JSON cartridge files. When changing cartridge content (`task.json`), you must fully restart the server. The `pkill` + restart pattern sometimes leaves zombie processes holding the port. Use this to force a clean restart:

```bash
lsof -ti:8001 | xargs kill -9; sleep 3; /home/vinga/projects/makaronas/venv/bin/python -m uvicorn backend.main:app --host 0.0.0.0 --port 8001 --reload &
```

Always verify the new process started by checking the PID in the startup log.

**Reveal text gotcha:** The green "Išvados" box on the reveal screen renders from `reveal.key_lesson` in the cartridge — NOT from the terminal phase's `trickster_content`. Both fields exist and are easy to confuse. If you update the reveal conclusions, update `reveal.key_lesson` — that's what the frontend displays. The `trickster_content` on the terminal phase appears as the Trickster's message above the green box.

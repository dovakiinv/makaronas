# Investigation Task Redesign — Continuous Dialogue

*Design intent for refactoring investigation tasks to use a single continuous AI dialogue.*

## The Problem

The current investigation task ("Sek pinigus") breaks the conversation into multiple phases:
1. AI dialogue (discuss framing) → phase transition
2. Static investigation (find Herald clue) → submit → phase transition
3. AI dialogue (discuss Herald) → phase transition
4. Static investigation (find Progress clue) → submit → phase transition
5. AI dialogue (discuss Progress) → phase transition
6. AI dialogue (synthesis) → phase transition
7. Static reveal

Each transition resets the dialogue, loses conversational context, and creates a jarring UX. The student builds rapport with Makaronas, discovers something, then gets yanked into a fresh conversation.

## The Solution

**One continuous AI dialogue** from start to finish. The investigation trees appear and disappear in the content panel as Makaronas guides the student, controlled by Trickster tool calls.

### Flow

```
Student opens task
  → Both articles visible in content panel
  → Makaronas opens dialogue: "Du portalai. Vienas įvykis. Ką tu čia matai?"
  → Student discusses framing with Makaronas
  → Makaronas calls show_investigation("herald")
    → Investigation tree for Žaliasis Heroldas appears in content panel (above articles)
    → Makaronas says "Tyrinėk — kas stovi už Žaliojo Heroldo?"
  → Student explores tree, clicks key finding (TrailBound)
    → Finding appears as a message in the dialogue (auto-submitted)
    → Makaronas responds: "Radai kai ką. Kodėl tai svarbu?"
  → Student explains the connection
  → Makaronas calls show_investigation("progress")
    → Herald tree collapses/dims, Progress tree appears
    → Makaronas says "Vieną giją radai. Dabar — Miesto Pažangos Žinios."
  → Student explores, finds Harland Ventures
    → Finding auto-submitted to dialogue
    → Makaronas asks about the chain, pushes for precision
  → Student articulates the ownership chain
  → Makaronas asks: "Ar kuris nors iš jų meluoja?"
  → Student discusses synthesis
  → Makaronas calls complete_task()
    → Reveal appears
```

### New Trickster Tool Calls

The Trickster already has `transition_phase`. New tools for investigation:

1. **`show_investigation`** — shows an investigation tree in the content panel
   - Parameter: tree identifier (e.g., "herald", "progress")
   - Frontend receives this as an SSE tool call event, renders the tree
   - Previous tree collapses/dims but stays accessible

2. **Key finding click → auto-message** — when student clicks a key finding in the tree, it auto-submits as a student message in the dialogue (e.g., "Radau: TrailBound Outdoor rengia festivalius Žalgirio parke ir praras pagrindinę renginių vietą jei parkas bus užstatytas.")

### Architecture Changes

**Backend:**
- New tool definition in the Trickster tool set for `show_investigation`
- Investigation tree data needs to be available in the AI phase context (currently only available in investigation phases)
- The single AI phase needs access to all search result blocks

**Frontend:**
- Investigation tree rendering triggered by SSE tool call events, not phase transitions
- Key finding clicks send a message to the ongoing dialogue instead of marking for submission
- No separate investigation controls panel — findings go straight to the conversation
- Content panel updates without interrupting the dialogue in the interaction panel

**Cartridge format:**
- The task becomes a single AI phase with investigation tree data embedded
- Or: investigation trees defined as task-level resources, referenced by the tool calls

### What This Enables

- **Natural conversation flow** — no jarring phase breaks
- **Makaronas can adapt** — if student finds something unexpected first, Makaronas can follow their lead
- **Grey zone engagement** — student can push back, go on tangents, and Makaronas follows without being forced to transition
- **Simplified cartridge** — one phase instead of seven
- **Reusable pattern** — any task that mixes investigation with dialogue benefits

### What This Does NOT Change

- The investigation tree UI itself (search results, expand/collapse, dead ends)
- The article content or financial chains
- The evaluation rubric or pass conditions
- The reveal content

### Implementation — Don't Overcomplicate This

The cartridge system is already flexible enough. This is NOT a major refactor — it's a new cartridge that uses existing infrastructure differently:

1. **One AI freeform phase** with all search result blocks in `visible_blocks` (hidden initially via CSS/JS)
2. **One new Trickster tool** (`show_investigation`) — tells the frontend to reveal a subset of search result blocks. Small addition to `trickster.py` and the SSE handler.
3. **Key finding clicks** post a message to the dialogue instead of marking for submission. Small change in `investigation.js`.
4. **Build as `task-follow-money-002`** — new cartridge using the new pattern, don't retrofit the old one.

The cartridge format doesn't need to change. The search result blocks are already supported. The tool call infrastructure is already built (V5). The frontend already renders search results and handles SSE tool call events.

**Total new code:** one tool definition, one SSE event handler, one click-to-message bridge. That's it.

### Decision

Park this. Sketch the other 4 tasks first, then come back and build the new cartridge. The continuous-dialogue pattern may apply to more than just investigation — knowing how the other tasks work will inform the design.

---

*Written: 2026-03-21*
*Status: Design intent captured, not yet implemented*

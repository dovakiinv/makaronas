# Makaronas 2.0 — Roadmap

*Tracking progress through the vision documents and build phases.*
*Reference: [PLATFORM_VISION.md](./PLATFORM_VISION.md) for full spec.*
*Reference: [TEAM_ROADMAP.md](./TEAM_ROADMAP.md) for team-facing roadmap and task tracks.*
*Reference: [AUTH.md](./AUTH.md) for identity roadmap (anonymous MVP → persistent identity).*

---

## MVP Scope

**Target:** 5-school trial (~150-300 students)

The MVP delivers a working student experience: students play through tasks with the Trickster, get tricked, learn from the reveal. Teachers have basic admin tools to assign tasks. The AI Composer, Roadmap Engine, and full evaluation intelligence come after the trial.

Vinga builds the plumbing and 4 story-linked MVP tasks (the "Mokytojas Vaitkus" arc) that prove the patterns. The team builds content on top of those patterns, polishes the UI, and builds the teacher experience.

**Identity model:** MVP uses anonymous per-session access — no student accounts, no persistent identity. Features requiring persistent identity (cross-session radar profiles, prerequisite enforcement, per-student teacher views) are deferred to post-trial. See [AUTH.md](./AUTH.md) for the full identity roadmap and transition plan.

---

## Phase 1: Foundation — *Vinga*

- [x] **V1 — Platform Architecture & API Foundation**
  - System design, API contracts, project structure
  - Define interfaces the AI layer needs
  - `models.py` — single source of truth for all model IDs (family names in code, IDs in one file)
  - Hooks for auth/DB/sessions (stubs)

- [x] **V2 — Task Definition Format (The Cartridge Spec)**
  - Task schema: AI-driven / static / hybrid
  - Multimodal content blocks: text, image, audio, video_transcript, meme_template
  - Metadata, tags, evaluation rubrics, prompt hooks
  - Validation rules
  - Reference tasks as proof of concept
  - *Blocked by: V1* ✓

## Phase 2: AI Core — *Vinga*

- [x] **V3 — AI Integration Layer**
  - Model provider abstraction (Gemini, Claude, swappable)
  - Prompt loading from `prompts/` directory (plain Markdown, model-specific variants)
  - **Prompt existence validation:** V2 warns when `ai_driven`/`hybrid` cartridges lack a prompt directory. V3 must enforce — if V3 can't load prompts for a task, that task cannot serve AI phases. Hard error at prompt load time, not runtime.
  - Context management: layering, prioritisation, token budget trimming
  - Conversation history injection
  - Prompt assembly pipeline: base + model variant + task + context → API call
  - Shared infrastructure for Trickster + Composer (design for both, build for Trickster)
  - Input/output safety guardrails (jailbreak detection, PII scrubbing)
  - CacheLayer hook interface (define once access patterns are known — prompts, profiles, task metadata)
  - `prompts/README.md` — guide for team on editing prompts
  - *Blocked by: V2* ✓

## Phase 3: Student Stream — *Vinga*

- [x] **V5 — Trickster AI Engine**
  - Persona management, per-task prompt architecture
  - Multi-turn dialogue, student history adaptation
  - Freeform evaluation against rubrics
  - Medium-specific voice (narrator, friend, commenter)
  - Fourth wall break (AI literacy moment)
  - *Blocked by: V3* ✓
  - *Note (V5): Task-switch state reset was fixed in V4 Phase 1c — `/next` endpoint now resets exchanges, turn_intensities, prompt_snapshots, and generated_artifacts when switching tasks. Task history intentionally persists.*

- [x] **V4 — Student Game Experience** *(scaffold)*
  - **Stack: Plain HTML + CSS + vanilla JS**, served from FastAPI's `static/` directory
  - Task rendering across medium types (including multimodal: image, audio, meme)
  - Social media feed renderers, meme renderer, search result tree, generic block fallback
  - Session flow, task transitions, page-load recovery
  - Trickster dialogue interface (SSE streaming — POST fetch + ReadableStream for /respond, EventSource for /debrief)
  - All 4 interaction types: button, freeform, investigation, generation (empathy flip)
  - Post-task flow: debrief streaming → reveal display → next task
  - Error recovery, rate limit handling, static fallback, skip-task option
  - Lithuanian i18n, accessibility (ARIA, keyboard navigation, focus management)
  - Browser-first, functional but not polished — no framework, no build step
  - *Blocked by: V5* ✓

- [~] **4 MVP Tasks — "Mokytojas Vaitkus" Story Arc**
  - One incident, four angles, one network. Each task teaches a different medium of manipulation through a connected narrative about a teacher who read a privacy policy and got discredited for it.
  - [x] Task 1: Two Articles — source analysis, funding trails, selective omission (investigation tree)
  - [x] Task 2: Comment Section + Protest Photo — bot detection, troll tactics, AI-generated image analysis
  - [ ] Task 3: Recap + Bot Network Visualization + Fake Bank Statement — visual recap of how manufactured narratives spread, fake financial document analysis
  - [ ] Task 4: Deepfake Video — synthetic media debunked by source verification, not pixel analysis
  - *Blocked by: V5, V4* ✓
  - *See [MVP_STORY.md](./MVP_STORY.md) for the full story design*
  - *The 6 archetype patterns (empathy flip, clean check, guided analysis, etc.) remain as post-MVP task types*
  - *Tasks come before V6 — the evaluation layer must be informed by real teaching patterns, not theory*

- [ ] **V6 — Evaluation & Session Intelligence**
  - **Session-level student evaluation:** cross-task pattern analysis after a teacher-defined task bundle (the "session" — e.g., 3 tasks for today's lesson). Surfaces which manipulation patterns the student fell for repeatedly, where they improved, growth-framed language (not grades). "Facts from Data, Personalization from AI" — platform counts patterns programmatically, AI wraps them in personalised growth narrative.
  - **Teacher-facing class aggregation:** anonymous patterns across students in a session. Which tasks had the highest trick success rate, which manipulation patterns the class struggles with, which students copy-pasted without analysis vs. engaged critically.
  - **Per-task debrief refinement** is NOT V6 — that's a task authoring concern handled during archetype creation. The Trickster's post-task moment is content, not infrastructure.
  - *Deferred to post-trial: radar profiles, cross-session pattern recognition, growth tracking — these require persistent student identity (see [AUTH.md](./AUTH.md))*
  - *Blocked by: 4 MVP Tasks (V6 scope is informed by real evaluation data from playable tasks)*

## Phase 4: Teacher Stream — *Team (post-archetypes)*

- [ ] **V7 — Teacher Dashboard**
  - Library browsing with filters
  - Task assignment to classes
  - Class-level anonymous insights display
  - Functional for trial — no Composer integration yet
  - *Blocked by: V4 scaffold + V6 (needs evaluation data and class aggregation)*

- [ ] **Teacher-Configurable Tasks** *(post-trial)*
  - Teachers create tasks from template structures with their own content (articles, images, comments)
  - Template cartridges with placeholder content blocks — teacher fills in the article, patterns are auto-detected or manually tagged
  - Validation that teacher-supplied content meets safety boundaries
  - *Architecture already supports this — cartridge format separates structure from content. Trickster prompts must be written generically (reference "the article" not specific content) to enable this path.*
  - *Blocked by: 4 MVP Tasks (templates need proven task structures to templatise)*

- [ ] **V8 — Composer AI (Teacher Assistant)** *(post-trial)*
  - RAG over the task library
  - Natural language → task sequence mapping
  - Pedagogical sequencing logic
  - Safe Slots (topic injection)
  - Reasoning explanation ("I chose this because...")
  - Refinement dialogue
  - *Blocked by: V3, V2, and sufficient task library*

- [ ] **V9 — Roadmap Engine** *(post-trial)*
  - Pre-built roadmap definitions
  - Custom path creation and editing
  - Difficulty curve algorithms
  - Prerequisite/dependency logic — *runtime enforcement requires persistent student identity (see [AUTH.md](./AUTH.md)). V2 carries prerequisite metadata; V9 enforces it.*
  - Time estimation
  - *Blocked by: V2, V8*

## Phase 5: Content & Handoff

- [ ] **V10 — Task Library Expansion** *(Team, parallel from Phase 2)*
  - New tasks built on proven patterns from the 4 MVP tasks
  - Task library taxonomy (triggers, techniques, mediums) — validated against `content/taxonomy.json`
  - Evergreen content guidelines and quality standards
  - New archetype patterns: empathy flip, clean check, guided analysis, adversarial dialogue
  - Target: ~15-20 total tasks for trial (4 MVP story tasks + team-authored expansions)
  - *Team can start drafting content once V2 lands*
  - *Team can build and test tasks once MVP tasks land*

- [ ] **V11 — Content Authoring & Contribution** *(spec only)*
  - Task templates enforcing cartridge format
  - Internal authoring tool design
  - Review/approval pipeline
  - Teacher contribution flow (future)
  - *Spec for team — Vinga defines, team builds*

- [ ] **V12 — Localization & Regional Adaptation** *(spec only)*
  - Multi-language architecture (LT, LV, EN)
  - Cultural adaptation patterns
  - Regional context packs
  - AI response language handling
  - *Spec for team — Vinga defines, team builds*

## Post-Trial: Cost & Deployment

- [ ] **AI Cost Projection Document**
  - Cost per student per session (by model choice)
  - Monthly cost at 5 schools (trial), 100 schools, and 800 schools
  - Cost levers (model selection, static/AI ratio, context tuning)
  - Recommendations for budget-conscious deployment
  - *Blocked by: trial data (needs real usage and per-task token profiles)*
  - *Audience: funding team — they need this before scaling beyond the 5-school trial*

---

## Dependency Map

```
V1 ✓ ──→ V2 ✓ ──→ V3 ✓ ──→ V5 ✓ ──→ V4 ✓ ──→ 4 MVP tasks (in progress) ──→ V6
                        │                         Tasks 1+2 ✓                  │
                        │      ┌────────────────────────────────────────────────┘
                        │      │
                        │      ▼
                        │   TEAM: V10 content expansion
                        │   TEAM: V7 teacher dashboard
                        │   TEAM: V4 UI polish
                        │   TEAM: V12 localization
                        │
                        └──→ (post-trial) V8 Composer ──→ V9 Roadmap Engine
```

---

## Legend

- [ ] Not started
- [~] In progress
- [x] Complete
- *(scaffold)* — Vinga builds functional minimum; team polishes
- *(spec only)* — Vinga writes the spec; team implements
- *(post-trial)* — Deferred until after 5-school trial

## Notes

- V10 (content) runs in parallel — drafting starts after V2, full building starts after MVP tasks
- Each vision document gets broken into phase plans for implementation
- "Complete" means vision document written, reviewed, and phases planned
- Implementation of each vision follows its own phase plan
- See [TEAM_ROADMAP.md](./TEAM_ROADMAP.md) for the team-facing view with task tracks

---

*Last updated: 2026-04-01*

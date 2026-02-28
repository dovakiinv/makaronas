# Makaronas 2.0 — Roadmap

*Tracking progress through the vision documents and build phases.*
*Reference: [PLATFORM_VISION.md](./PLATFORM_VISION.md) for full spec.*
*Reference: [TEAM_ROADMAP.md](./TEAM_ROADMAP.md) for team-facing roadmap and task tracks.*
*Reference: [AUTH.md](./AUTH.md) for identity roadmap (anonymous MVP → persistent identity).*

---

## MVP Scope

**Target:** 5-school trial (~150-300 students)

The MVP delivers a working student experience: students play through tasks with the Trickster, get tricked, learn from the reveal. Teachers have basic admin tools to assign tasks. The AI Composer, Roadmap Engine, and full evaluation intelligence come after the trial.

Vinga builds the plumbing and 6 archetype tasks that prove the patterns. The team builds content on top of those patterns, polishes the UI, and builds the teacher experience.

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

- [ ] **V3 — AI Integration Layer**
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
  - *Blocked by: V2*

## Phase 3: Student Stream — *Vinga*

- [ ] **V5 — Trickster AI Engine**
  - Persona management, per-task prompt architecture
  - Multi-turn dialogue, student history adaptation
  - Freeform evaluation against rubrics
  - Medium-specific voice (narrator, friend, commenter)
  - Fourth wall break (AI literacy moment)
  - *Blocked by: V3*

- [ ] **V4 — Student Game Experience** *(scaffold)*
  - **Stack: Plain HTML + CSS + vanilla JS**, served from FastAPI's `static/` directory
  - Task rendering across medium types (including multimodal: image, audio, meme)
  - **Social media feed renderers:** Many planned tasks (astroturfing detection, fear escalation feeds, fake petitions) present content as simulated social media posts with usernames, timestamps, engagement counts, comment threads. V4 needs PresentationBlock renderers for feed-style content — the backend serves these via the open type pattern, V4 renders them. See `FutureTaskList.md` for the 8 task concepts driving this need.
  - Session flow, task transitions
  - Trickster dialogue interface (SSE streaming via `EventSource` API)
  - Reflection/journal prompts
  - Browser-first, functional but not polished — no framework, no build step
  - *If post-trial needs demand complex interactions (drag, real-time state), revisit framework choice with real evidence*
  - *Blocked by: V5*

- [ ] **V6 — Evaluation (MVP thin)**
  - Per-task evaluation results (rubric-based)
  - Session summary for students
  - Anonymous class-level aggregation for teachers
  - *Deferred to post-trial: radar profiles, cross-session pattern recognition, growth tracking — these require persistent student identity (see [AUTH.md](./AUTH.md))*
  - *Blocked by: V5*

- [ ] **6 Archetype Tasks**
  - Adversarial Dialogue — multi-turn Trickster chat (e.g., The Phantom Quote)
  - Investigation — guided discovery through branching content (e.g., Follow the Money)
  - Empathy Flip — student creates manipulation, AI evaluates
  - Clean Check — legitimate content, tests false-positive instinct
  - Guided Analysis — student analyses group dynamics with AI guidance, not by posting replies (e.g., The Wedge, redesigned 2026-02-25). Show neutralising reply patterns as examples, simulate forum reactions to different approaches.
  - Visual Manipulation — image-based deception: framing, cropping, context removal (e.g., The Misleading Frame — new concept 2026-02-25). Photograph from one angle misleads, second image reveals fuller context.
  - *Blocked by: V5, V4*
  - *These are the reference implementations the team builds on*
  - *V2 ships 6 reference cartridges (2 full, 4 skeletons) that prove the format — archetypes are the playable end-to-end versions*

## Phase 4: Teacher Stream — *Team (post-archetypes)*

- [ ] **V7 — Teacher Dashboard**
  - Library browsing with filters
  - Task assignment to classes
  - Class-level anonymous insights display
  - Functional for trial — no Composer integration yet
  - *Blocked by: V4 scaffold + V6 thin (needs student-facing patterns and evaluation data)*

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
  - New tasks built on the 6 archetype patterns
  - Task library taxonomy (triggers, techniques, mediums) — validated against `content/taxonomy.json`
  - Evergreen content guidelines and quality standards
  - Target: ~15-20 total tasks for trial (6 archetypes + 9-14 team-authored)
  - *Note: The Wedge archetype was redesigned (analysis-based, not reply-based) and The Misleading Frame (image task) was added — see V2 vision doc §2.4 for details*
  - *Team can start drafting content once V2 lands*
  - *Team can build and test tasks once archetypes land*

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
V1 ✓ ──→ V2 ✓ ──→ V3 (next) ──→ V5 ──→ V4 scaffold ──→ V6 thin ──→ 6 archetypes
                        │                                              │
                        │      ┌───────────────────────────────────────┘
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

- V10 (content) runs in parallel — drafting starts after V2, full building starts after archetypes
- Each vision document gets broken into phase plans for implementation
- "Complete" means vision document written, reviewed, and phases planned
- Implementation of each vision follows its own phase plan
- See [TEAM_ROADMAP.md](./TEAM_ROADMAP.md) for the team-facing view with task tracks

---

*Last updated: 2026-02-26*

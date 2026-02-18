# Makaronas 2.0 — Roadmap

*Tracking progress through the vision documents and build phases.*
*Reference: [PLATFORM_VISION.md](./PLATFORM_VISION.md) for full spec.*

---

## Phase 1: Foundation

- [ ] **V1 — Platform Architecture & API Foundation**
  - System design, API contracts, project structure
  - Define interfaces the AI layer needs
  - `models.py` — single source of truth for all model IDs (family names in code, IDs in one file)
  - Hooks for auth/DB/sessions (stubs)
  - *Blocked by: nothing — start here*

- [ ] **V2 — Task Definition Format (The Cartridge Spec)**
  - Task schema: AI-driven / static / hybrid
  - Multimodal content blocks: text, image, audio, video_transcript, meme_template
  - Metadata, tags, evaluation rubrics, prompt hooks
  - Validation rules
  - Reference tasks as proof of concept
  - *Blocked by: V1 (needs to know where tasks live in the architecture)*

## Phase 2: AI Core

- [ ] **V3 — AI Integration Layer**
  - Model provider abstraction (Gemini, Claude, swappable)
  - Prompt loading from `prompts/` directory (plain Markdown, model-specific variants)
  - Context management: layering, prioritisation, token budget trimming
  - Conversation history injection
  - Prompt assembly pipeline: base + model variant + task + context → API call
  - Shared infrastructure for Trickster + Composer
  - Input/output safety guardrails (jailbreak detection, PII scrubbing)
  - CacheLayer hook interface (define once access patterns are known — prompts, profiles, task metadata)
  - `prompts/README.md` — guide for team on editing prompts
  - *Blocked by: V1, V2*

## Phase 3: Student Stream

- [ ] **V5 — Trickster AI Engine**
  - Persona management, per-task prompt architecture
  - Multi-turn dialogue, student history adaptation
  - Freeform evaluation against rubrics
  - Medium-specific voice (narrator, friend, commenter)
  - Fourth wall break (AI literacy moment)
  - *Blocked by: V3*

- [ ] **V4 — Student Game Experience** *(scaffold)*
  - Task rendering across medium types (including multimodal: image, audio, meme)
  - Session flow, task transitions
  - Trickster dialogue interface
  - Reflection/journal prompts
  - Browser-first, functional but not polished
  - *Blocked by: V5 (needs to know what Trickster outputs look like)*

- [ ] **V6 — Evaluation & Growth Intelligence**
  - Checklist/rubric evaluation system
  - Radar profile (trigger vulnerability mapping)
  - Pattern recognition across sessions
  - Growth tracking
  - Anonymous class-level aggregation
  - *Blocked by: V5 (builds on Trickster evaluation output)*

## Phase 4: Teacher Stream

- [ ] **V8 — Composer AI (Teacher Assistant)**
  - RAG over the task library
  - Natural language → task sequence mapping
  - Pedagogical sequencing logic
  - Safe Slots (topic injection)
  - Reasoning explanation ("I chose this because...")
  - Refinement dialogue
  - *Blocked by: V3, V2 (needs AI layer + task format)*

- [ ] **V7 — Teacher Dashboard** *(scaffold)*
  - Library browsing with filters
  - Roadmap management UI
  - Class-level anonymous insights display
  - Composer chat integration
  - Functional but not polished
  - *Blocked by: V8 (needs to know what Composer outputs)*

- [ ] **V9 — Roadmap Engine**
  - Pre-built roadmap definitions
  - Custom path creation and editing
  - Difficulty curve algorithms
  - Prerequisite/dependency logic
  - Time estimation
  - *Blocked by: V2, V8 (needs task format + Composer integration)*

## Phase 5: Content & Handoff

- [ ] **V10 — Task Library: Taxonomy & Content**
  - Full taxonomy (triggers, techniques, mediums)
  - Evergreen content guidelines
  - Quality standards for authored tasks
  - 10-15 fully authored AI-driven tasks
  - 25+ outlined with taxonomy tags (placeholders for team)
  - *Can be worked on in parallel from Phase 2 onward*

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

## Post-Build: Cost & Deployment

- [ ] **AI Cost Projection Document**
  - Cost per student per session (by model choice)
  - Monthly cost at 5 schools (trial), 100 schools, and 800 schools
  - Cost levers (model selection, static/AI ratio, context tuning)
  - Recommendations for budget-conscious deployment
  - *Blocked by: V10 (needs task mix and per-task token profiles)*
  - *Audience: funding team — they need this before scaling beyond the 5-school trial*
  - *Must be delivered before Vinga's involvement ends (April 2026)*

---

## Legend

- [ ] Not started
- [~] In progress
- [x] Complete
- *(scaffold)* — Vinga builds functional minimum; team polishes
- *(spec only)* — Vinga writes the spec; team implements

## Notes

- V10 (content) runs in parallel with engineering phases
- Each vision document gets broken into phase plans for implementation
- "Complete" means vision document written, reviewed, and phases planned
- Implementation of each vision follows its own phase plan

---

*Last updated: 2026-02-18*

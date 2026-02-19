# Makaronas 2.0: Platform Vision Specification

*From prototype to platform. From trainer to simulator.*

---

## 1. What This Document Is

This is the master specification for the full Makaronas platform — a living reference that captures the architectural vision, the 12 vision documents, roles, build order, and design principles agreed upon during the February 2026 planning sessions.

Each vision document (V1-V12) will be written separately with full detail. This document is the map that holds them together.

---

## 2. The Mission

**Train the Pause.**

The platform teaches teenagers to recognise media manipulation — not by lecturing, but by letting them experience it firsthand. An adversarial AI (the Trickster) tries to trick them. Win or lose, both outcomes become learning moments.

The ultimate victory condition for a student isn't "I fact-checked this." It is **"I felt the urge to share this, and I stopped."**

---

## 3. The Dual Literacy Goal

Two groups fund and drive this project:

- **Information literacy group** (project team) — focused on teaching recognition of media manipulation, misinformation patterns, and structural media bias.
- **AI literacy group** (funders) — originally focused on deepfake recognition, now broadened to understanding AI as both a tool and a threat.

**These goals converge in the platform itself:**

- Students experience AI literacy by being manipulated by an AI (the Trickster), then having the AI explain exactly how it did it — and what it means that a machine can do this at scale.
- Teachers experience AI literacy by collaborating with an AI (the Composer) that transparently helps them plan curriculum — showing its reasoning, accepting overrides, modelling the right human-AI relationship.

The platform doesn't teach *about* AI as a separate subject. **The platform IS the AI literacy lesson.**

---

## 4. Design Principles

### 4.1 Meet Them Where They Psychologically Live

Teenagers don't read headlines. They live on TikTok, group chats, Discord, Instagram stories, memes. The platform's tasks must be set in mediums teenagers actually encounter daily. But:

### 4.2 Evoke, Don't Imitate

No fake phone UI. No simulated TikTok clone. Teenagers have razor-sharp radar for adults pretending to be their world — it's patronising and dates itself instantly. The platform uses clean, purpose-built interfaces that **evoke** each medium's dynamics without pixel-perfect imitation. Theatre staging, not movie sets.

### 4.3 Evergreen Content

Task scenarios must avoid topical references that shift, change, or look different in hindsight. No current news, no trending topics, no references to specific platforms by name in content. The **psychological triggers** are evergreen (urgency, belonging, injustice, greed, cynicism). The **techniques** are evergreen (cherry-picking, fabrication, wedge-driving). Scenarios should be fictional but realistic, set in a world close enough to be relatable, distant enough to not date.

### 4.4 Moral High Ground

The Trickster is adversarial but honest. After the reveal, it plays fair. The platform itself must never use manipulation techniques on students — no surveilling scroll speed, no false claims about their emotional state, no dark patterns. The teaching works because the Trickster is transparent about its tricks after the fact. If the platform itself is manipulative, we lose the right to teach about manipulation.

### 4.5 Calibrated Judgment, Not Cynicism

Some tasks should contain no manipulation at all. The student must learn to distinguish genuine content from manipulated content. Without "clean" tasks, we train paranoia, not critical thinking. The platform teaches the pause, not the rejection.

### 4.6 The Fourth Wall Break (AI Literacy Moment)

At key moments — particularly in the debrief — the Trickster drops character entirely:

> "I'm an AI. I just adapted that response specifically to your previous answers. A human couldn't do this to 300 students simultaneously. But I can. That's the point."

This transforms every task into an AI literacy lesson without needing a separate module.

### 4.7 The Core AI Principle

**Every AI-driven feature relies on the same capability: understanding and responding to what this specific student actually said and did, in their own words, across time.**

This is what separates AI-driven tasks from static content. Static content teaches *about* manipulation. AI creates the *experience* of being manipulated, resisting it, attempting it, and reflecting on your own patterns. The difference is the difference between reading about swimming and being in the water.

This principle guides every AI design decision in the platform:

- **Adversarial conversation** — The Trickster doesn't accept "something feels off." It pushes back: "What specifically? The source is real. The data is accurate. What's your problem with it?" The student must defend their skepticism against a capable opponent. Recognition becomes instinct through practice, not exposure.
- **The mirror across tasks** — AI holds the student's full history and confronts them with their own patterns: "In Task 1 you said you'd never trust a headline. In Task 3 you did exactly that. The medium changed. Your behavior didn't."
- **The empathy flip** — After catching manipulation, the student is asked to *create* it: "Write me a headline that would make your classmates share without reading." AI evaluates the attempt. Nothing teaches recognition like attempted creation.
- **The living group chat** — AI doesn't just evaluate a response — it continues the conversation as other participants. Social pressure, pile-ons, the cost of speaking up. The student feels the dynamics, not just reads about them.
- **Metacognitive prediction** — Before a task, the student predicts their own vulnerability. After, AI holds up the gap between prediction and reality: "You said you wouldn't fall for this. You lasted eight seconds."
- **Adaptive targeting** — Two students in the same class get different experiences. One is vulnerable to authority signals, the other to belonging triggers. AI shifts the attack vector to each student's actual weakness.
- **Guided discovery** — When a student catches one manipulation but misses others, AI doesn't say "wrong, try again" and doesn't give the answer. It narrows the search: "You found the emotional language. Good. Now look at the numbers — what's the source for that 40% claim?" The student still does the finding, but they know roughly where to look and what to look for. This is the difference between a teacher who says "try harder" and one who points you at the right paragraph. Without this, students disengage — they know they haven't found the answer but have no idea what they're even looking for. AI eliminates that dead zone where learning goes to die.
- **The "nothing is wrong" curveball** — Some tasks have no manipulation. If the student falsely accuses legitimate content, AI catches it: "I didn't trick you this time. Your own paranoia did. Critical thinking isn't distrust — it's judgment."

Every task design should be tested against this principle: **does this task need AI because it responds to what *this* student specifically said and did?** If a static branching path would work just as well, it should be static. AI is reserved for where it's irreplaceable.

---

## 5. Architecture Overview

### 5.1 Model Registry (Single Source of Truth)

All AI model identifiers live in a single `models.py` file — the only place where specific model IDs (e.g., `claude-sonnet-4-6`, `gemini-3-flash-preview`) are defined. The rest of the codebase refers to models by **family name** only (e.g., `CLAUDE_SONNET`, `GEMINI_FLASH`).

When a model version changes, one file is updated. Nothing else touches model IDs. This pattern is proven across Vinga's other projects and is non-negotiable for maintainability.

```python
# models.py — the ONLY place model IDs live
CLAUDE_SONNET = "claude-sonnet-4-6"
CLAUDE_HAIKU = "claude-haiku-4-5-20251001"
GEMINI_FLASH = "gemini-3-flash-preview"
GEMINI_FLASH_LITE = "gemini-2.0-flash-lite"

# Usage everywhere else:
# from models import CLAUDE_SONNET
# Never hardcode "claude-sonnet-4-6" anywhere else.
```

This applies to both Trickster and Composer engines, and any future AI integrations (image generation, audio, embeddings).

### 5.2 Separation of Concerns

Frontend and backend are fully separate, communicating via REST API. The AI layer is a backend service that both the student experience and teacher experience consume through clean interfaces.

```
FRONTEND (Student App + Teacher Dashboard)
    │
    │ REST API
    │
BACKEND
    ├── API Layer (routes, request handling)
    ├── AI Integration Layer (model abstraction, prompts, context)
    │   ├── Trickster Engine (adversarial, student-facing)
    │   └── Composer Engine (helpful, teacher-facing)
    ├── Task Engine (content storage, retrieval, metadata)
    ├── Roadmap Engine (sequencing, difficulty curves)
    ├── Evaluation Engine (rubrics, radar profile, growth)
    └── HOOKS (stubs with clear interfaces)
        ├── Auth (returns fake user — team implements real auth)
        ├── Database Adapter (in-memory — team swaps for real DB)
        ├── Session/User Management (minimal — team extends)
        └── File Storage (local — team swaps for cloud)
```

### 5.3 Prompt Architecture (Team-Accessible, Model-Aware)

Two distinct concerns live in the prompt system, owned by different people:

1. **Prompt content** (team-accessible) — The actual wording, persona instructions, evaluation criteria, reveal text. The team should be able to find, read, and edit these without touching code. Written in plain Markdown.
2. **Context management** (Vinga's domain) — How much context each task gets, how history is layered, what's prioritised when approaching token limits, what prior task data is injected. This is architectural and lives in the AI integration layer (V3).

**File structure: one directory per task, one file per model family.**

```
prompts/
├── trickster/
│   ├── persona_base.md          # shared Trickster persona (all models)
│   ├── persona_claude.md        # Claude-specific persona tuning
│   └── persona_gemini.md        # Gemini-specific persona tuning
├── composer/
│   ├── base.md                  # shared Composer system prompt
│   ├── claude.md
│   └── gemini.md
├── tasks/
│   ├── 001_clickbait_trap/
│   │   ├── task.md              # shared task context, content, rubric
│   │   ├── claude.md            # Claude-tuned prompt for this task
│   │   └── gemini.md            # Gemini-tuned prompt for this task
│   ├── 002_cherry_pick/
│   │   ├── task.md
│   │   ├── claude.md
│   │   └── gemini.md
│   └── ...
└── README.md                    # how to write/edit prompts (for team)
```

**Design principles:**

- **Plain Markdown files** — no YAML, no JSON, no special syntax. The team opens a `.md` file, reads it, edits it. Git diff shows exactly what changed.
- **Model-specific files are optional** — if `claude.md` doesn't exist for a task, the system falls back to `task.md` (the base). Model files contain only the delta — adjustments needed for that model family's strengths/quirks.
- **Versioning through git** — no separate prompt versioning system. Git commit history is the version history. The team can see when a prompt changed and revert if needed.
- **The code never contains prompt text** — prompt loading is a function that reads from the `prompts/` directory. The AI integration layer (V3) handles assembly: base persona + model variant + task prompt + context injection. But the raw text lives in files the team can touch.
- **README as guide** — `prompts/README.md` explains the structure, what each file does, how to test changes, and what not to touch (context management markers that the engine uses for injection points).

**Why model-specific prompts matter:** Different model families respond differently to the same instructions. Claude tends to be more cautious and needs explicit permission to be adversarial. Gemini may need different formatting for structured output. The team can experiment with model-specific tuning without risk — the base prompt is always the fallback.

**Context management (Vinga's layer) sits between prompts and the API call:**

```
Team writes:          Vinga's layer assembles:           API receives:
                      ┌──────────────────────┐
persona_base.md ──────┤                      │
persona_claude.md ────┤  Context Manager     │
task.md ──────────────┤  (V3)                ├──────── Final prompt
claude.md ────────────┤                      │         (assembled,
student history ──────┤  · Layers & merges   │          token-budgeted,
prior task data ──────┤  · Prioritises       │          with history)
session state ────────┤  · Trims to budget   │
                      └──────────────────────┘
```

The team controls what goes into each file. Vinga controls how they're assembled, what context is added, and what gets cut when approaching token limits.

**Affects:** V2 (task cartridge references its prompt directory), V3 (AI layer — prompt loading, assembly, context management), V5 (Trickster — persona prompts), V8 (Composer — system prompts), V11 (authoring — prompt templates for new tasks).

### 5.5 The Two AIs

**The Trickster** (student-facing)
- Adversarial, theatrical, in-character
- Knows the current task deeply, doesn't expose the library
- Evaluates freeform responses against rubrics
- Adapts tone based on student performance history
- Shifts voice across mediums (narrator, "friend," commenter)
- Must be fast — students won't wait for responses in chat simulations

**The Composer** (teacher-facing)
- Helpful, transparent, pedagogical
- Knows the entire task library — every tag, trigger, difficulty rating
- Maps natural language to task sequences (RAG over the library)
- Explains its reasoning ("I chose this because...")
- Accepts refinement ("make it shorter," "swap in a meme task")
- Remembers class context across sessions (what was already covered)
- Supports "Safe Slots" — teacher injects a neutral topic, AI wraps tasks around it

### 5.6 Task Architecture

A task is defined as structured data (the "cartridge"):

```
Task Definition:
├── id, title, version
├── type: "ai_driven" | "static" | "hybrid"
├── trigger: emotional vector (urgency, belonging, injustice, greed, cynicism...)
├── technique: manipulation method (cherry-pick, fabrication, wedge, framing...)
├── medium: presentation format (chat, feed, article, meme, video, comment...)
├── difficulty: 1-5 scale
├── time_estimate: minutes
├── evergreen: boolean
├── tags: searchable metadata (age range, subject tie-in, region...)
├── content: the scenario material (structured per medium type)
├── evaluation: rubric, checklist items, mandatory items, pass conditions
├── trickster_prompts: persona config, reveal text, adaptation rules
└── static_paths: (for static/hybrid tasks) deterministic branching logic
```

Both AI-driven and static tasks use the same format. The `type` field determines whether the Trickster AI is called for evaluation or whether branching is deterministic.

### 5.7 Multimodality & Learning Styles

Humans learn differently — visual, auditory, reading/writing, kinaesthetic. The platform must account for this, not as an afterthought but as a design constraint from the start.

**What this means in practice:**

- **Visual**: Some tasks involve images — misleading graphs, decontextualised photos, memes, AI-generated images. The task content schema must support image assets as first-class content blocks, not bolted-on extras.
- **Auditory**: Voice notes in group chat tasks, podcast-style clips, tone-of-voice manipulation (calm authority vs. urgent alarm). Audio assets supported in the content schema.
- **Reading/writing**: The current prototype's strength — articles, posts, freeform text responses. Remains the backbone.
- **Kinaesthetic**: The hardest to integrate digitally. Closest analogues: the physical act of scrolling, the muscle memory of tapping "share," the investigative click-path in research tasks (Task 4's tree). The Freeze Frame concept (scrubbing a timeline to identify the tipping point) is a kinaesthetic interaction.

**Implementation approach:**

- **Pre-generated assets preferred** — AI image/audio generation is not called at runtime for every student. Tasks that need visual/audio content use pre-generated assets baked into the task cartridge. This keeps costs predictable and quality controlled.
- **AI generation for task authoring** — When creating new tasks, AI image/audio generation can be used to produce the assets. But they're reviewed, curated, and stored — not generated live.
- **Content blocks in the cartridge spec** — The task format (V2) must support typed content blocks: `text`, `image`, `audio`, `video_transcript`, `meme_template`, etc. The student frontend (V4) renders them appropriately per medium.
- **Not every task needs every modality** — A group chat task might be text-only. A meme task is image-first. A voice note task is audio-first. The modality serves the scenario, not the other way around.

**Accessibility as curriculum, not accommodation.** The combination of typed content blocks, modality alternatives, and adaptive AI opens a deeper opportunity: full curricula tailored to specific accessibility groups. A blind student doesn't get a degraded version of a graph task — they get a learning path where auditory manipulation (tone of authority, cadence of urgency, podcast framing) is the primary attack vector. A deaf student gets curricula emphasising visual manipulation (misleading data visualisations, decontextualised images, written social pressure). The platform doesn't accommodate these students — it teaches them through the modality where they are strongest and most vulnerable. This requires: semantic API responses (content, not rendering instructions), text descriptions for all visual assets in the cartridge format, audio descriptions for visual tricks that preserve the deceptive framing, evaluation based on what the student *said* not how they *interacted*, and configurable timeout budgets per modality (voice interaction is slower than typing).

**Affects:** V2 (task format — content block types, modality alternatives per block), V4 (frontend — rendering multimodal content), V5 (Trickster — evaluating responses to visual/audio stimuli, modality-aware persona), V10 (task library — which tasks use which modalities, accessibility-specific curricula), V11 (authoring — asset pipeline, alternative content requirements).

---

## 6. The 12 Vision Documents

### Vinga's Deliverables (AI-Driven, Built to Completion)

| Vision | Title | Scope |
|--------|-------|-------|
| **V1** | Platform Architecture & API Foundation | System design, API contracts, project structure, deployment. Defines interfaces the AI layer needs. Hooks for auth/DB/sessions. Team picks tech stack details. |
| **V2** | Task Definition Format (The Cartridge Spec) | The data schema for tasks. AI-driven vs static vs hybrid. Metadata, evaluation rubrics, prompt hooks. Validation rules. Reference tasks as proof of concept. |
| **V3** | AI Integration Layer | Model abstraction (swap Gemini/Claude/etc without rewriting). Prompt template management (versioned, testable). Conversation history and context injection. Token budget management. The shared infrastructure both AIs need. |
| **V5** | Trickster AI Engine | Persona management, prompt architecture per task type. Multi-turn dialogue handling. Adaptation based on student history. Evaluation logic for freeform responses. Medium-specific voice shifting. The fourth wall break. Performance tuning. |
| **V6** | Evaluation & Growth Intelligence | AI-powered assessment of freeform responses. The checklist/rubric system. The "radar profile" — which triggers catch this student. Pattern recognition across sessions. Growth tracking. Anonymous aggregation for class-level insights. |
| **V8** | Composer AI (Teacher Assistant) | RAG over the task library. Natural language curriculum planning. Pedagogical sequencing logic. Safe Slots (topic injection). Explanation of reasoning. Refinement dialogue. Class history awareness. |

### Team Deliverables (Scaffold from Vinga, Team Builds Out)

| Vision | Title | Scope |
|--------|-------|-------|
| **V4** | Student Game Experience | UI/UX, task rendering across medium types. Session flow, task transitions. Trickster dialogue interface. Reflection/journal prompts. Browser-first, accessible. Vinga builds functional scaffold; team polishes. |
| **V7** | Teacher Dashboard | Library browsing with filters. Roadmap management. Class-level anonymous insights. Task preview. Vinga builds functional scaffold showing Composer integration; team polishes. |
| **V9** | Roadmap Engine | Pre-built roadmaps. Custom path creation. Difficulty curve algorithms. Prerequisite logic. Time estimation. Sits between Composer and Task Library. |

### Spec Only (Vinga Defines, Team Implements)

| Vision | Title | Scope |
|--------|-------|-------|
| **V10** | Task Library: Taxonomy & Content | Full taxonomy of triggers, techniques, mediums. Evergreen content guidelines. Quality standards. Vinga authors AI-driven tasks. Static task outlines as placeholders for team/content authors. |
| **V11** | Content Authoring & Contribution | Task templates enforcing cartridge format. Internal authoring tool. Review/approval pipeline. Teacher contribution flow (future). |
| **V12** | Localization & Regional Adaptation | Multi-language structure (Lithuanian, Latvian, English). Cultural adaptation patterns. Regional context packs. How AI responses handle language. |

---

## 7. Build Order & Dependencies

### Phase 1: Foundation
1. **V1 — Platform Architecture** — The skeleton. Everything plugs into this.
2. **V2 — Task Format** — The cartridge spec. Defines what everything operates on.

### Phase 2: AI Core
3. **V3 — AI Integration Layer** — Shared infrastructure for both AIs.

### Phase 3: Student Stream
4. **V5 + V4 — Trickster + Student Experience** — Built together. Need to see the Trickster *in* the student UI to verify it works. Just enough frontend to feel the AI in context.
5. **V6 — Evaluation & Growth** — Builds on Trickster output.

### Phase 4: Teacher Stream
6. **V8 + V7 — Composer + Teacher Dashboard** — Built together. Need to see the Composer in context to verify the interaction.
7. **V9 — Roadmap Engine** — Connects Composer recommendations to task sequencing.

### Phase 5: Content & Handoff
8. **V10 — Task Library** — Author AI-driven tasks. Taxonomy and outlines for the rest.
9. **V11 — Authoring System** — Spec for team.
10. **V12 — Localization** — Spec for team.

### Dependency Map

```
V1 (Architecture) ─────────────────────────────────────┐
    │                                                    │
V2 (Task Format) ──────────────────────┐                │
    │                                  │                │
V3 (AI Layer) ─────────────┐           │                │
    │                      │           │                │
    ├── V5 (Trickster) ────┤           │                │
    │       │              │           │                │
    │   V4 (Student UX) ──┤           │                │
    │       │              │           │                │
    │   V6 (Evaluation) ──┘           │                │
    │                                  │                │
    ├── V8 (Composer) ────┐            │                │
    │                     │            │                │
    │   V9 (Roadmap) ─────┤            │                │
    │       │             │            │                │
    │   V7 (Teacher UX) ──┘            │                │
    │                                  │                │
V10 (Task Library) ────────────────────┘                │
    │                                                    │
V11 (Authoring) ────────────────────────────────────────┤
                                                        │
V12 (Localization) ────────────────────────────────────-┘
```

V10 (content) can be worked on in parallel with everything — it's mostly writing, not engineering.

---

## 8. Handoff Strategy

### 8.1 Timeline

**Vinga's involvement ends approximately April 2026.** Everything must be built, documented, and handed off so the team can manage, modify, and scale the platform independently. No AI specialist on call after handoff.

This means every deliverable must be self-explanatory. The team should be able to:
- Modify prompts and see different AI behavior (without understanding context management)
- Add new static tasks using the cartridge template (without touching code)
- Swap models by changing one line in `models.py` and optionally writing a model-specific prompt file
- Replace stubs with real implementations by following the interface contracts
- Debug AI issues by reading logs (token usage, model family, latency)
- Understand *why* things are built the way they are (vision docs explain rationale, not just structure)

### 8.2 What Vinga Delivers

A **running application** where:
- AI-driven tasks work end-to-end (student plays, Trickster responds, evaluation runs)
- The Composer chat works (teacher describes a need, gets a roadmap)
- The evaluation radar shows student patterns
- Every non-AI piece has a stub with a clear interface and documentation

### 8.3 What the Team Receives

- Working codebase with real AI functionality
- Clear `# TEAM: replace this` markers on every stub
- API contracts that won't change (the AI layer's interfaces are stable)
- Vision documents for each component they own (rationale included, not just specs)
- `prompts/README.md` — how to edit prompts, test changes, add model variants
- `content/tasks/TEMPLATE/` — empty cartridge template for authoring new tasks
- Freedom to choose frontend framework, database, auth provider, deployment strategy

### 8.4 Post-Handoff Self-Sufficiency

Things the team **can** do without Vinga:
- Edit any prompt file (adjust tone, wording, evaluation criteria)
- Author new static tasks using the cartridge template
- Swap AI models (update `models.py`, optionally write model-specific prompts)
- Implement auth, database, deployment
- Build and redesign the frontend
- Add new pre-built roadmaps

Things that **would benefit from AI expertise** (but are documented enough to attempt):
- Authoring new AI-driven tasks (evaluation rubrics, context requirements)
- Tuning context management (what gets injected, token budgets)
- Optimising for new model families with different strengths
- Scaling the Composer's library awareness as the task count grows

---

## 9. Scale & Cost

### 9.1 Target Scale

- **Trial:** 5 schools (funded by current 2K EUR — tests student/teacher reaction)
- **First rollout:** 100 schools
- **Full target:** 800 schools
- **Current funding:** 2,000 EUR (British Embassy) — covers prototype, initial build, and 5-school trial
- **AI API costs at 100+ schools are not covered by current funding** and will need separate budget

### 9.2 Cost Projection Deliverable

A full AI cost projection will be produced alongside V10 (Task Library), once the task mix (AI-driven vs static) and per-task token profiles are defined. This document will include:

- Cost per student per session (by model choice)
- Monthly cost at 100 schools and 800 schools
- Cost levers (model selection, static/AI task ratio, context size tuning)
- Recommendations for budget-conscious deployment

The static/AI task ratio is the primary cost lever. More static tasks = lower per-student cost, but weaker AI engagement. The ratio should be an informed decision by the team, not a default.

---

## 10. Resolved Design Decisions

Decisions made during planning sessions, recorded here for reference:

| Decision | Resolution | Decided in |
|----------|-----------|------------|
| Streaming | SSE for all AI responses (Trickster, Composer, debrief) | V1 planning |
| Student memory | Two layers: session (24h TTL) + learning profile (persistent, GDPR-safe) | V1 planning |
| Multi-tenant | Yes, from day one. Interfaces include `school_id`. Target: 800 schools. | V1 planning |
| Model registry | Single `models.py`, family names in code, IDs in one file | Architecture discussion |
| Prompt storage | Plain Markdown files, one dir per task, one file per model family. Git versioning. | Architecture discussion |
| Multimodality | Pre-generated assets in task cartridges. Content block types in schema. | Architecture discussion |
| Asset delivery | Backend serves from local filesystem. `FileStorage` hook for team to swap to CDN. | V1 planning |
| Cold start | No profile → no adaptation. First session establishes baseline. Flash Lite for cold-start sessions. | V1 planning |

---

## 11. Open Design Decisions

These will be resolved as each vision document is written:

1. **Static vs AI task ratio** — What percentage of the initial 40 tasks are AI-driven vs static? Directly impacts cost. Resolved in V10.
2. **Composer memory scope** — Does the Composer remember a single teacher's history? A school's? How is context bounded? Resolved in V8.
3. **Task Library V1 scope** — How many tasks are fully authored vs outlined? Recommend 10-15 fully built, 25+ outlined with taxonomy tags. Resolved in V10.

---

*Document version: 1.1*
*Created: 2026-02-18*
*Updated: 2026-02-18 (streaming, memory layers, scale target, resolved decisions)*
*Author: Vinga + Claude (planning session)*

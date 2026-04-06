# Makaronas — Team Roadmap

*What's built, what's next, and where you come in.*

---

## The Big Picture

Makaronas teaches teenagers to recognize media manipulation through adversarial AI. A character called **the Trickster** tries to fool students with manipulated content — then reveals how and why, turning every failure into a learning moment.

**MVP target:** 5-school trial (~150-300 students)

---

## Overall Progress

```
████████████████████░░░░░░░░░░  ~65% to MVP
```

### What's Done

| What | Completed | What it means |
|------|-----------|---------------|
| **V1 — Platform Architecture** | Feb 2026 | The server skeleton, API structure, database/auth hooks ready for real implementations |
| **V2 — Task Format (Cartridges)** | Feb 2026 | The JSON format that defines every task — content, phases, evaluation rubrics, AI behaviour. 6 reference tasks created (2 fully fleshed out, 4 skeletons) |
| **V3 — AI Integration** | Feb 2026 | The AI brain — connects to Gemini and Claude, manages conversations, handles safety, assembles prompts |
| **V5 — Trickster Engine** | Mar 2026 | The Trickster's personality — adapts voice to each task type, tracks intensity, breaks the fourth wall to teach AI literacy, handles clean (no-trick) tasks, supports images |

| **V4 — Student Experience** | Mar 2026 | The web interface students interact with — task display, Trickster chat, investigation trees, social media renderers, image lightbox, SSE streaming |
| **Tasks 1+2 — Petryla Story** | Mar 2026 | Two articles investigation + comment section with protest photo analysis — playable end-to-end |

**1,680 automated tests passing.** The plumbing is solid.

### What This Means in Plain Terms

The backend AND the student-facing web interface are built and tested. The Trickster holds adversarial conversations in Lithuanian, adapts to different task types, evaluates student responses, and streams responses in real-time. Students can already play through Tasks 1 and 2 of the Petryla story arc end-to-end.

**What's left: 2 more tasks, evaluation infrastructure, and teacher tools.**

---

## What's Left for MVP

### Must-Have (blocks the trial)

| What | Status | What it means |
|------|--------|---------------|
| **Tasks 3+4 — Petryla Story** | Not started | Bot network visualization + fake bank statement, then deepfake video |
| **V6 — Evaluation (thin)** | Not started | Per-task scores, session summaries, anonymous class stats for teachers |
| **V7 — Teacher Dashboard** | Not started | Browse task library, assign tasks to classes, view class-level results |
| **V10 — Content Expansion** | Can start now | New tasks following proven patterns. Target: ~15-20 total for trial |

### Nice-to-Have (can ship after trial starts)

| What | Notes |
|------|-------|
| V8 — Composer AI (teacher assistant) | Teachers pick tasks manually for trial |
| V9 — Roadmap Engine (learning paths) | Hand-curated sequences for trial |
| V11 — Content Authoring Tool | Team uses cartridge templates directly |
| V12 — Full Localization | Lithuanian first, multi-language later |
| AI Cost Projection | Needs real trial usage data |

---

## The 4 MVP Tasks — "Mokytojas Petryla"

One incident, four angles, one network. A teacher read a privacy policy, built his own system, got discredited by the company he rejected. Each task teaches a different medium of manipulation through this connected story.

| # | Task | Medium | What the student does | Status |
|---|------|--------|----------------------|--------|
| 1 | **Two Articles** | Text (articles) | Analyses two outlets covering the same incident — one corporate-funded, one ideologically biased. Investigates funding trails and the privacy policy. | ✓ Done |
| 2 | **Comment Section + Protest Photo** | Social media + image | Identifies bots, trolls, and genuine sharers. Analyses an AI-generated protest photo — learns visual tells are temporary, source verification is permanent. | ✓ Done |
| 3 | **Recap + Bot Network + Bank Statement** | Visualization + image | Visual recap of how the manufactured narrative spread. Analyses a fake bank statement "proving" Petryla was paid by competitors. | Not started |
| 4 | **Deepfake Video** | Video | A fake surveillance video of Petryla meeting a competitor CEO. Debunked not by pixel analysis but by checking the calendar — the CEO was on another continent that day. | Not started |

Skills compound across tasks: source-checking from Task 1 becomes a tool in Task 4. Bot patterns from Task 2 help identify the fake channel in Task 4.

See [MVP_STORY.md](./MVP_STORY.md) for the full story design.

### Future Task Patterns (Post-MVP)

The platform supports more task archetypes beyond the Petryla story:
- **Empathy Flip** — student creates manipulation, AI evaluates (see [EMPATHY_FLIP_CONCEPT.md](./EMPATHY_FLIP_CONCEPT.md))
- **Clean Check** — no manipulation present, tests false-positive instinct
- **Adversarial Dialogue** — real-time debate with the Trickster
- **Guided Analysis** — analyse group dynamics and how manipulation spreads

New tasks are built by writing cartridges (JSON + content), not new code.

---

## What Can Start Now

### Content drafting (V2 is done)

The task format is defined. Content work can start right now:

- [ ] **Drafting task scenarios** — stories, articles, social media posts, dialogue scripts
- [ ] **Sourcing/creating media assets** — images, graphs, audio clips
- [ ] **Mapping content taxonomy** — which triggers, techniques, and mediums each task covers
- [ ] **Writing evaluation rubrics** — what should the student catch? What counts as a good response?

Reference: `content/tasks/template/` has the authoring guide and blank template.

### After MVP tasks land: Full building & testing

Once all 4 MVP tasks are playable end-to-end:

- [ ] **Build new tasks** — write a cartridge, test it live, iterate
- [ ] **Polish the student UI** — the V4 scaffold is functional but rough
- [ ] **Build the teacher dashboard (V7)** — library browsing, task assignment, class insights
- [ ] **Start localization groundwork** — Lithuanian is primary, architecture supports language packs

---

## MVP Path

```
  DONE ✓                        TO BUILD
  ──────────────────────        ────────────────────────────────────────────

  V1 Platform Architecture
  V2 Task Format                Next up               Step 2            Step 3
  V3 AI Integration             ──────────────        ──────────────    ──────────
  V5 Trickster Engine
  V4 Student UI                 Tasks 3+4             V7 Teacher        TRIAL
                                  Bot network viz       Dashboard        READY
  Tasks 1+2 playable              Bank statement        Browse library
  1,680 tests passing             Deepfake video        Assign tasks   15-20 tasks
                                                        Class results  Student UI polished
                                V6 Evaluation                          Teacher tools working
                                  Per-task scores     V10 Content
                                  Session summaries     Expansion
                                  Class-level stats     10-15 more
                                                        tasks

                             ◄── Content drafting can happen in parallel ──►
                                (scenarios, media assets, rubrics, taxonomy)
```

**The critical path:** Tasks 3+4 → V6 → V7 + Content Expansion → Trial

Content drafting runs in parallel throughout.

---

## Full Project Map (Including Post-Trial)

```
DONE ✓                          TO BUILD
──────────────────────          ──────────────────────────

V1 Platform        ─┐
V2 Task Format     ─┤
V3 AI Integration  ─┤──→  Tasks 3+4  ──→  V6 Evaluation (thin)
V5 Trickster Engine─┤                              │
V4 Student UI      ─┤                              ▼
Tasks 1+2          ─┘                     V7 Teacher Dashboard
                                          V10 Content Expansion
                                                    │
                                             ═══════╧═══════
                                              5-SCHOOL TRIAL
                                             ═══════════════
                                                    │
                                                    ▼
                                       V8 Composer AI (post-trial)
                                       V9 Roadmap Engine (post-trial)
                                       V12 Localization (post-trial)
```

---

## Architecture Quick Reference

```
backend/
  api/           — Server routes (student, teacher, admin)
  ai/            — AI layer (Trickster, safety, context, prompts)
  tasks/         — Task loading, validation, registry
  hooks/         — Swappable infrastructure (auth, database, sessions)
  models.py      — AI model configuration (single source of truth)

content/
  tasks/         — Task cartridges (each task = folder with task.json + assets)
  taxonomy.json  — Known triggers, techniques, mediums

static/          — Student UI (plain HTML + CSS + vanilla JS, served by FastAPI)

prompts/         — AI prompt files (plain Markdown, editable by anyone)
```

**Key principle:** Prompts are plain Markdown files. You edit them like any text file. Git tracks changes. No special syntax, no code required.

---

## How We Work

- **GitHub Issues** are the task board
- **Assign yourself** before starting work to avoid collisions
- **The cartridge spec is the contract** — if your task follows the schema and passes validation, it works
- **Prompts are plain Markdown** — the team can tune AI behaviour without touching code

---

## What's NOT in MVP

These are real and planned, but they ship **after** the 5-school trial. The architecture has hooks for all of them — they're deferred, not cancelled.

| What | Why deferred |
|------|-------------|
| **V8 — Composer AI** (teacher assistant) | Teachers select and sequence tasks manually for trial |
| **V9 — Roadmap Engine** (learning paths) | Hand-curated sequences are enough for 5 schools |
| **V11 — Content Authoring Tool** | Team uses cartridge templates and JSON directly |
| **V12 — Full Localization** | Lithuanian only for trial; multi-language comes after |
| **AI Cost Projection** | Needs real trial usage data to be meaningful |
| **Cross-session student profiles** | MVP uses anonymous per-session access — no student accounts. Radar profiles, growth tracking, and prerequisite enforcement all need persistent identity |
| **Advanced evaluation** (radar profiles, pattern recognition) | MVP has per-task scores + session summaries. Deeper analytics need more data and persistent identity |
| **Additional archetype tasks** | Empathy flip, clean check, guided analysis, adversarial dialogue — these patterns exist in the engine but aren't in the MVP story arc |

**The line is clear:** MVP delivers a working student experience with the Trickster through the 4-task Petryla story arc, basic evaluation, and enough teacher tools to run a trial. Everything that needs real usage data or persistent student identity waits until after.

---

*Last updated: 2026-04-01*

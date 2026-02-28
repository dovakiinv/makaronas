# The Makaronas Framework
*Engineering Principles for an Educational AI Platform*

## Purpose

This framework establishes the design and engineering principles for the Makaronas platform. It is the lens through which every vision document, phase plan, and implementation decision is reviewed.

Makaronas is not a generic web app. It is an educational tool that uses AI to teach teenagers about media manipulation. The students are minors. The AI is adversarial by design. The content touches sensitive topics. Every principle here exists to ensure we build something that is **safe, effective, honest, and maintainable** — in that order.

---

## Scope

### What We're Building
An interactive platform where AI-driven adversarial dialogue teaches students to recognise manipulation in the spaces where they actually encounter it — social media feeds, comment sections, group chats, shared screenshots, and the casual claims that reach them through friends and family. The techniques are timeless (cherry-picked citations, fabricated quotes, structural bias, social engineering), but the delivery channel is peer-to-peer: someone you trust shares something they didn't verify, and the instinct is to pass it on. The platform trains students to break that chain — to verify before spreading, to pause before sharing.

### Who It's For
- **Students:** Ages 15-18 (initial scope). May expand to younger and older age groups in future. All design decisions assume the youngest end of the range.
- **Teachers:** Plan curriculum, select task sequences, view anonymous class-level insights.
- **Content authors:** Author new tasks using templates and the cartridge format.

### Scale
- **Trial:** 5 schools (~150-300 students)
- **First rollout:** 100 schools (~3,000-6,000 students)
- **Full target:** 800 schools (~24,000-48,000 students)

### What We're NOT Building
- A fact-checking tool
- A social media monitoring system
- A student surveillance platform
- A grading system

---

## The Principles

### 1. Train the Pause (The Mission)
*Motto: "The victory is the hesitation before the share button."*

The entire goal of this platform — and of AI within it — is to help students and teachers deeply understand information manipulation: its methods, its goals, the organisations and agendas behind it, the individuals and groups that benefit politically or financially from shifting public opinions, moods, and sentiments. False narratives don't appear spontaneously — they are manufactured, funded, and distributed with purpose. The platform teaches resilience against this by building genuine understanding, not just pattern recognition.

Every feature, every task, every AI interaction serves this purpose: teaching students to pause before reacting. Not to distrust everything — to think before they act. The pause is the outcome. Understanding is the path.
- **Experience over lecture.** Students learn by being tricked, not by being told what tricks look like. They experience manipulation firsthand, then understand how and why it was constructed.
- **Depth over checklists.** The goal isn't a memorised list of manipulation techniques — it's understanding how false narratives are created, who benefits, and why they spread. The methods are the surface; the motives and structures behind them are the lesson.
- **Growth over scores.** No points, no grades, no leaderboards. The platform tracks patterns and growth, not performance.
- **Break the chain.** Misinformation reaches teenagers through people they trust — a friend's story, a screenshot in a group chat, a parent's casual remark. The platform teaches students to verify before passing something on, not just to recognise manipulation when they see it.

### 2. Moral High Ground (The Non-Negotiable)
*Motto: "If the platform manipulates the student, we've already lost."*

The Trickster is adversarial. The platform is not. This distinction is sacred.
- **No dark patterns.** No tracking scroll speed, no false claims about emotional state, no surveillance disguised as pedagogy.
- **Honest reveals.** After every trick, the Trickster tells the student exactly what it did and how. No hidden manipulation that isn't explained.
- **Respect the student.** Teenagers are sharp. They know when they're being patronised, surveilled, or manipulated for real. The platform earns trust by being transparent about its methods.
- **Content boundaries.** No real harmful misinformation (health, violence, self-harm). Manipulation is theatrical and clearly educational. Topics are relevant but not triggering.

### 3. Student Data as Sacred Trust (GDPR & Beyond)
*Motto: "We are custodians of minors' data. Act accordingly."*

This is not optional. This is not a checkbox. This is the foundation.
- **Data minimisation.** Store only what's needed for adaptive teaching. No raw conversation text persisted beyond the 24-hour session.
- **Pseudonymisation.** Students are opaque IDs. The platform never sees names, emails, or any PII. The auth system maps identity — the platform doesn't.
- **Right to deletion.** One API call wipes everything. Structurally enforced, not policy-dependent.
- **Right to access.** Students (or their guardians) can export all stored data in a readable format.
- **Purpose limitation.** Learning profile data is for adaptive teaching only. Never for grading, behavioural assessment, disciplinary action, or sharing beyond the teacher's anonymous class view.
- **No PII in logs.** Request logs use opaque IDs. AI call logs track tokens and latency, not content.
- **Consent at the gate.** The platform assumes consent when a valid session exists. Obtaining consent is the auth layer's responsibility — the platform's responsibility is to deserve it.
- **Design for audit.** Every data flow should be explainable to a regulator. If you can't draw the diagram of where student data goes and who can see it, the architecture is wrong.

### 4. Evergreen Content (The Shelf Life Rule)
*Motto: "If it dates within a year, it doesn't belong."*

Misinformation tactics are timeless. The scenarios that illustrate them should be too.
- **No current events.** No trending topics, no real public figures, no references to specific recent incidents.
- **No platform-specific branding.** Scenarios evoke "a social media feed" or "a group chat," not "TikTok" or "WhatsApp" by name. Platforms come and go; the manipulation grammar stays.
- **Fictional but realistic.** Scenarios should feel plausible without being traceable to real events.
- **Psychological triggers are the constant.** Urgency, belonging, injustice, greed, cynicism — these don't change. Build around them.

### 5. Evoke, Don't Imitate (The UI Rule)
*Motto: "Theatre staging, not movie sets."*

The platform presents tasks in mediums teenagers recognise — but never pretends to be those mediums.
- **No fake phone UI.** No pixel-perfect TikTok clones, no simulated notification bars. Teenagers detect adult cosplay instantly and disengage.
- **Evocative design.** A chat task feels like a chat — message bubbles, timestamps, usernames. But it's clearly the platform, not a screenshot of WhatsApp.
- **Honest framing.** The platform is a training environment. It says so. The Trickster is the liar, not the platform.

### 6. The Core AI Principle (Why AI Matters Here)
*Motto: "AI is the teacher, not the examiner. It earns its cost by engaging with what this student actually said and did."*

AI is not used for novelty or evaluation. It's used where it's irreplaceable — for teaching through engagement. The AI challenges, guides, and pushes back in real-time, helping each student internalize the lessons through lived adversarial experience. Evaluation is a byproduct of that engagement, not its purpose. Static content can describe manipulation. AI creates the experience of encountering it, resisting it, and understanding why it was built.
- **Adversarial conversation.** AI pushes back on student skepticism: "What specifically? The source is real." This forces the student to articulate and defend their reasoning — the teaching happens in that struggle. Static branching can't do this.
- **Guided discovery.** AI narrows the search when a student is stuck, pointing them toward what to look for without giving the answer. The goal is internalization, not correct answers.
- **The mirror across tasks.** AI holds student history and confronts them with their own patterns across sessions.
- **Adaptive targeting.** AI shifts the attack vector to each student's specific vulnerability.
- **The empathy flip.** AI guides students who try to create manipulation themselves — understanding the creator's perspective deepens the lesson.
- **Calibrated judgment.** Some tasks have no manipulation. AI helps students recognize when content is legitimate — teaching discernment, not paranoia.
- **The litmus test.** For every AI-driven feature, ask: "Would a static branching path work just as well?" If yes, make it static. AI is reserved for where it's irreplaceable — where the student needs to be engaged, challenged, and guided in real-time.

### 7. The Dual Literacy (Platform as Teacher)
*Motto: "The platform IS the AI literacy lesson."*

The platform teaches both information literacy and AI literacy — not as separate modules, but through its own existence.
- **Students experience AI manipulation firsthand.** The Trickster is an AI. It tells them so. The lesson is: a machine just did this to you, and it can do it to millions simultaneously.
- **Teachers experience AI collaboration.** The Composer shows its reasoning, accepts overrides, explains its choices. It models what healthy human-AI interaction looks like.
- **The fourth wall break.** At key moments, the Trickster drops character entirely and speaks as an AI about what AI can do. This is the deepest teaching moment.

### 8. Team Accessibility (The Handoff Rule)
*Motto: "If the team can't change it without calling the original author, it's not done."*

The platform will be maintained by a technical team without a dedicated AI specialist. Everything must be accessible.
- **Prompts are plain Markdown.** No special syntax, no code. The team opens a file, reads it, edits it. Git tracks the changes.
- **Model swapping is one line.** Change the model ID in `models.py`, optionally write a model-specific prompt file. Done.
- **Architecture is documented with rationale.** Not just "what" but "why." Future maintainers need to understand the reasoning behind decisions, not just follow instructions.
- **Hooks are clearly marked.** Every stub says what it does, what replaces it, and what interface to satisfy.
- **AI complexity is encapsulated.** The context management layer (layering, budgeting, prioritisation) is complex, but it's documented well enough for a competent developer to debug and modify.

### 9. Cost Consciousness (The Token Tax)
*Motto: "Every AI call has a price. Every price needs justification."*

At 800 schools, careless token usage becomes a budget crisis.
- **Model tiering.** Use the cheapest model that meets quality requirements. Flash Lite for simple evaluations, stronger models for complex dialogue.
- **Per-task model selection.** Not every task needs the most capable model. The cartridge format specifies which model family a task prefers.
- **Static where possible.** Static tasks cost zero per student. The AI/static ratio is a deliberate cost lever, not an afterthought.
- **Token budgets.** The context manager enforces budgets per AI call. If context exceeds the budget, it trims intelligently rather than failing.
- **Usage logging.** Every AI call logs: model used, tokens in, tokens out, latency. Cost visibility from day one.

### 10. Graceful Degradation (The Fallback)
*Motto: "AI is an enhancement, not a dependency."*

AI will fail. Models go down. Rate limits hit. The student should never see a blank screen.
- **Static fallback.** If the Trickster can't respond, the task falls back to its static branching paths (if they exist) with a note that the AI is temporarily unavailable.
- **Timeout budgets.** AI calls have strict timeouts. A student waiting more than 5 seconds in a chat task has already disengaged. Better to show a graceful fallback than a spinner.
- **Error as guidance.** If AI fails, the error message tells the student (or teacher) what happened and what to do: "The AI is thinking too hard. Try again, or continue to the next task."

### 11. Structural Isolation (The Bulkhead Rule)
*Motto: "A broken prompt should never crash the platform."*

Architecture prevents cascading failures.
- **AI layer is isolated.** A bad prompt, a model timeout, or a provider outage affects AI responses only — not routing, not state management, not the teacher dashboard.
- **Hooks are boundaries.** Auth, database, storage are swappable because they're behind interfaces. A database migration doesn't touch AI code. An auth change doesn't touch task logic.
- **Frontend is independent.** The frontend consumes the API. It can be rebuilt, reskinned, or replaced without touching the backend.
- **Tasks are self-contained.** A broken task cartridge affects that task only. Other tasks continue working.

### 12. AI Output Safety (The Guardrail)
*Motto: "The Trickster is adversarial by design. The guardrails are not optional."*

Prompt instructions are suggestions to the model, not guarantees. For a platform where an adversarial AI talks to minors, safety must be enforced programmatically — not hoped for.
- **Output validation.** AI responses pass through a content safety check before reaching the student. Responses that cross content boundaries (real harm, real hate, real personal attacks) are caught and replaced with a safe fallback — not silently, but with a logged incident.
- **Topic boundaries are code, not prose.** The list of forbidden content areas (self-harm, real violence, sexual content, real-world radicalisation) is defined in a structured format the safety layer can check against — not buried in a prompt the model might ignore.
- **Escalation is bounded.** The Trickster adapts and pushes back — but there's a ceiling. The system tracks conversational intensity and intervenes if the adversarial pressure crosses a threshold, regardless of what the prompt says.
- **Prompt change regression.** Any change to Trickster prompts runs against a safety test suite before deployment. A prompt edit that passes the golden set for quality but fails the safety set does not ship.
- **Model change validation.** Swapping models (Principle 8) is easy. But a new model may behave differently under adversarial pressure. Model changes require a safety evaluation pass, not just a functional one.
- **Streaming changes the safety equation.** When AI responses stream to the student token-by-token (SSE, WebSocket), pre-delivery filtering is impossible without buffering latency. Every safety gate designed for complete-response checking must be re-evaluated for streaming. The canonical pattern: run the safety check post-completion on the accumulated response, and if it fails, emit a correction event (e.g., `redact`) that the frontend handles immediately — replacing the just-displayed content with a safe fallback. The student sees the system actively policing the AI, which itself reinforces the platform's educational mission (Principle 7). This applies to any current or future streaming interface.

### 13. Security by Design (The Locked Classroom)
*Motto: "We're teaching students to think like attackers. Assume they will."*

This platform handles minors' data, teacher curricula, and AI systems that students interact with directly. Security is not a feature — it's a constraint on every design decision.
- **Prompt injection defence.** Students type freeform text that reaches an AI. They will try to jailbreak the Trickster. Input sanitisation, output validation, and system prompt isolation are mandatory — not because students are malicious, but because we taught them to probe.
- **Tenant isolation.** A student in School A must never see data from School B. A teacher must never see another school's curricula. Multi-tenant boundaries are enforced at the data layer, not just the UI.
- **Least privilege.** Students see their own data. Teachers see anonymous class-level insights. Admins see school-level aggregates. No role sees more than it needs. API endpoints enforce this, not just the frontend.
- **No secrets in the client.** API keys, model credentials, and internal endpoints never reach the browser. The frontend is untrusted.
- **Rate limiting.** AI endpoints have per-student and per-school rate limits. A single student's runaway session must not exhaust the school's token budget or the platform's API quota.
- **Audit trail.** Authentication events, role changes, data exports, and data deletions are logged. Not for surveillance — for accountability when something goes wrong.
- **Error opacity.** Internal errors return generic messages to students. Stack traces, model names, and system paths never leak to the client. Debug information lives in server logs, not HTTP responses.
- **Database discipline.** Every query uses parameterised statements — no string interpolation, no exceptions. All database access goes through the data layer interface, never directly from route handlers. Schema migrations are reviewed for data exposure. Backup and restore procedures exist and are tested. Connection credentials are environment variables, never committed to source.
- **Dependency hygiene.** Third-party packages are pinned and reviewed. The attack surface of an educational platform used by minors is not the place for bleeding-edge dependencies.

### 14. Accessibility & Inclusion (The Open Door)
*Motto: "Educational infrastructure is for everyone."*

This platform will be used by diverse students across hundreds of schools.
- **Keyboard navigation.** Every interaction reachable without a mouse.
- **Screen reader support.** Content panels, buttons, chat messages — all properly labelled.
- **Lithuanian first and only (for now).** Lithuanian is the exclusive language for all content, UI, and AI interactions in the current build. All task cartridges, prompts, Trickster dialogue, teacher interface, and student-facing text are in Lithuanian. The architecture should not preclude future localisation (Latvian, English are eventual possibilities) — a locale field on cartridges and language-aware prompt loading are cheap to include. But no vision, plan, or implementation should spend effort on multi-language support, translation workflows, or locale switching. That's V12's problem. Build for Lithuanian. Leave the door open structurally. Don't walk through it yet.
- **Cognitive load.** Clear, calm UI. No visual overload. The Trickster's theatrics live in the text, not in flashing UI elements.
- **Browser-first.** Standard web application. Desktop browser is the primary target. Responsive design is nice-to-have, not a requirement. Mobile apps are a future consideration, not initial scope.
- **Voice-mode ready.** Blind students can interact with AI through voice without a screen reader — the conversational core of the platform is naturally voice-compatible. To keep this path open: API responses must be semantic (content, not rendering instructions), task cartridges must include text descriptions for all visual assets, evaluation must judge what the student *said* not how they *clicked*, and timeout budgets must be configurable per modality.

### 15. Multimodal Learning (The Whole Brain)
*Motto: "Not everyone learns by reading."*

The platform supports multiple learning modalities — but only where they serve the task.
- **Visual.** Misleading graphs, decontextualised images, memes, AI-generated images. Images are first-class content blocks, not decorations.
- **Auditory.** Voice notes, tone-of-voice manipulation, podcast clips. Audio assets supported in the task format.
- **Reading/writing.** The backbone. Articles, posts, freeform text responses.
- **Kinaesthetic (digital).** Investigation trees, timeline scrubbing, the physical act of typing a response under social pressure.
- **Pre-generated assets.** Multimodal content is authored and reviewed, not generated at runtime. Quality and cost are controlled.

### 16. Honest Engineering (The Pragmatism Principle)
*Motto: "Ship what works. Document what's missing. Don't pretend."*

This is a volunteer-built platform with real constraints. We build honestly within them.
- **Stubs are honest.** A fake auth service says "STUB — returns test user." It doesn't pretend to authenticate.
- **Scope is declared.** Each vision document says what's in scope and what's deliberately deferred. No "optional" items that create ambiguity.
- **Tradeoffs are documented.** When we choose speed over flexibility (or vice versa), we write down why. Future maintainers need the reasoning.
- **Technical debt is named.** If we take a shortcut, we label it. "This in-memory store won't survive a restart. See hooks/database.py for the interface the team implements."

### 17. Modularity & Maintainability (The Living System)
*Motto: "The format outlives the author. The system outlives the vision."*

This platform will be maintained, extended, and adapted by people who weren't in the room when the decisions were made. Every data format, interface, and component must be designed for change — not just for today's requirements.
- **Open taxonomies over closed enums.** Where values represent a growing domain (triggers, techniques, mediums, content types, interaction types), use open strings validated against a config, not schema-level enums. Adding a new trigger or content block type should never require a code release or schema migration.
- **Extensible data structures.** Formats that carry typed content (task cartridges, content blocks, interactions) should use an open type pattern: a `type` string plus a `data`/`config` dict. Known types get full validation; unknown types pass through with structural validation only. The backend doesn't gate on types it doesn't recognise — it loads, validates what it can, and passes everything to consumers. The frontend renders known types with specific components and unknown types with a graceful fallback.
- **Lifecycle over deletion.** Data referenced by other systems (tasks, roadmaps, profiles) should be deprecated, not deleted. Deprecation preserves reference integrity while hiding items from active use. Missing-but-referenced data is handled gracefully — log a warning, degrade, don't crash.
- **Hot-swappable content.** Content changes (new tasks, updated cartridges, revised prompts) should be deployable without server restart at production scale. Interfaces should accommodate reload even if the V2 implementation is simple.
- **Self-contained units.** Each task, each component, each module is independently understandable and independently replaceable. A broken unit affects only itself (see Principle 11). No hidden coupling, no inheritance chains, no shared mutable state between units.
- **Interfaces before implementations.** Every swappable component defines its contract as an interface (ABC, protocol, schema). The implementation behind it can change without rippling through consumers. This is proven by V1's hooks pattern — the same discipline applies to task formats, evaluation contracts, and any new extensibility point.
- **Derived paths are a single source of truth.** Never compute project root, content directory, or any structural path by chaining `.parent.parent.parent` from a file's location. These chains break silently when directory structure changes — the code still runs but points somewhere wrong. Compute the path once in one canonical place (e.g., `config.py`), and pass it as a parameter to everything that needs it. If a module needs to know where the project root is, it receives it as an argument — it never counts parent directories from its own `__file__`.
- **Rationale is part of the deliverable.** Code without rationale is unmaintainable. Every design decision, every "why not the obvious approach," every tradeoff is documented where future maintainers will find it — in the code (comments on non-obvious choices), in the vision documents (architectural rationale), and in implementation notes (deviations and lessons). The team inherits understanding, not just artifacts.

### 18. End-to-End Testing (The User Journey)
*Motto: "If nobody walked the path, the path doesn't exist."*

Unit tests prove components work. Contract tests prove interfaces hold. But neither proves the student's experience works from start to finish. This platform has user journeys that cross multiple systems — a student starts a session, receives a task, interacts across phases, gets evaluated, sees a reveal, and moves to the next task. If any seam fails, the experience breaks.
- **Journey tests, not just unit tests.** Every major user flow must have an end-to-end test that walks the full path: session creation → task loading → phase progression → interaction → evaluation → reveal → next task. These tests catch the integration failures that unit tests miss — the moment where the loader's output doesn't match what the frontend expects, or the evaluation engine receives a shape the rubric doesn't handle.
- **Student journey first.** The primary test suite follows the student: start session, get a task, make choices, respond freeform, receive AI evaluation, see the reveal, proceed. This is the critical path. If this breaks, nothing else matters.
- **Teacher journey second.** Browse library with filters, preview a task, build a roadmap, view class insights. The teacher doesn't interact with AI adversarially, but their experience must be coherent end-to-end.
- **Failure journeys matter.** Test what happens when AI fails mid-conversation. Test what happens when a student's session expires. Test what happens when a referenced task is deprecated. The graceful degradation path (Principle 10) must be tested, not just documented.
- **Real cartridges in tests.** Integration tests should load real reference cartridges, not synthetic test fixtures. If the reference cartridges work end-to-end, the format is proven. If they don't, the format has a gap that synthetic tests would have hidden.
- **Test at the API boundary.** End-to-end tests hit the API endpoints, not internal functions. The student frontend and teacher dashboard consume the API — the tests should consume it the same way. This catches serialisation issues, middleware interactions, and response envelope problems that internal tests skip.

### 19. AI Experience — AX (The Other User)
*Motto: "AI is a consumer of your interfaces. Design for it like you'd design for a human."*

This platform has two categories of users: humans (students, teachers, authors) and AI systems (Trickster, Composer, evaluation engine). Both consume the platform's interfaces. Both deserve thoughtful experience design. Poor UX loses human users. Poor AX produces bad AI behaviour — and in a platform where AI talks to minors, bad AI behaviour is not acceptable.
- **AI-consumed interfaces are designed, not accidental.** Task cartridges, evaluation rubrics, prompt structures, and API responses are all consumed by AI. Their structure should be as intentional as a UI layout — clear field names, unambiguous semantics, consistent patterns. If a field could mean two things, the AI will guess wrong half the time.
- **Clear success/failure signals.** When AI tools or interfaces are invoked, the result must clearly indicate success or failure. Ambiguous responses — empty results that could mean "nothing found" or "query failed," partial data that looks complete — cause AI to make confident wrong decisions. Every AI-consumed endpoint and data structure should make its state unambiguous.
- **Test AI behaviour, not just AI plumbing.** It's not enough to test that the Trickster receives the right prompt. Test that the Trickster *behaves correctly* given a well-formed cartridge — evaluates against the rubric, pushes back appropriately, reveals patterns accurately. Test that the Composer produces relevant task recommendations given a teacher's query. Test that the evaluation engine produces consistent judgments given the same student response. These are AX tests — they verify the AI's experience of consuming our interfaces produces correct behaviour.
- **Rubric testability.** Every evaluation rubric in a cartridge should be testable: given this student response, does the evaluation produce the expected outcome? Reference cartridges should include test cases — sample student responses with expected evaluation results. This is the AX equivalent of a UI test: "given this input, does the interface produce the right experience?"
- **Prompt-format coupling is a test target.** When cartridge content is injected into prompts, the combination must be tested. A cartridge that validates perfectly but produces garbled prompts when assembled by the context manager (V3) is an AX failure. Integration tests should verify the full chain: cartridge → prompt assembly → AI response → evaluation.
- **AI error messages are actionable.** When AI encounters a malformed input (bad rubric, missing content block, ambiguous phase transition), the error should tell the *author* what's wrong — not just log a stack trace. This is the AX equivalent of a good form validation message: "The rubric for phase 3 references pattern 'cherry_pick' but no pattern with that ID exists in patterns_embedded."
- **Facts from data, personalization from AI.** When ground truth exists as structured data — pattern counts in a rubric, evaluation results, task metadata, class statistics — the platform renders it programmatically. AI personalizes *around* the facts but never *generates* them. The Trickster says "I used 3 patterns" because the platform counted `patterns_embedded`; the AI adds "and you caught two of them" based on the student's responses. In a platform that teaches students to distrust misinformation, we cannot have the AI hallucinating facts about its own behaviour. This applies everywhere: reveal mechanics (V5), evaluation summaries (V6), Composer recommendations (V8), dashboard insights (V7).
- **Context continuity across boundaries.** When data flows between systems or phases, the receiving component must inherit full relevant state. A Trickster AI evaluating a student after static button phases must know which buttons were clicked. An evaluation engine scoring a hybrid task must know the full path the student took. A Composer responding to a teacher must know what tasks the class already completed. Silent context loss produces confident wrong behaviour — the AI doesn't know what it doesn't know, so it fills the gap with hallucination. Every system boundary must explicitly define what context crosses it and verify that it arrives intact.
- **Tool calls for AI-to-platform signals.** When an AI needs to signal the platform — phase transition, evaluation result, structured control flow — use the model's native tool/function calling mechanism, not in-band text markers embedded in the response. Tool call events are structurally separate from text content in both Gemini and Anthropic SDKs. Text-parsing approaches (e.g., scanning for `[COMPLETE]` tokens) are fragile, incompatible with streaming (the signal tokens reach the student before the backend can intercept them), and give the AI an ambiguous signaling interface. Tool calling gives the AI an unambiguous, typed way to declare intent — the AX equivalent of a well-designed form submission vs hoping the user types a keyword in a text field.

### 20. Boundary Validation (The Load-Time Gate)
*Motto: "If a student can encounter it, we validated it before they got there."*

Everything that enters the system — content, configuration, assets, identifiers — is validated at the boundary, not at runtime. A student should never see a broken task, a missing image, a dead-end phase, or a corrupted reference. The cost of validation at load time is negligible. The cost of a runtime failure in a classroom of 30 teenagers is a lesson derailed.
- **Structural integrity at load time.** Phase graphs are validated for reachability, terminal phases, and bounded cycles. A content author's typo in a phase transition ID must not trap a student in an inescapable loop. This validation happens when the cartridge loads, not when the student hits the broken phase.
- **Resource existence at load time.** If a task references an image, audio file, or prompt file, the loader verifies it exists on disk. A missing asset in a visual manipulation task isn't a cosmetic bug — the entire learning experience is broken, and the AI evaluates the student unfairly against content they couldn't see.
- **Identity consistency at load time.** When an identifier appears in multiple places (directory name and JSON field, URL path and database key), enforce exact match at the boundary. Divergent identifiers cause silent corruption — duplicate task references in student profiles, broken prerequisite chains, misrouted assets.
- **Path safety at load time.** File paths in content (asset references, prompt directory links) are validated against directory traversal and unsafe characters before the content enters the system. Security validation is a load-time gate, not a runtime filter (Framework Principle 13).
- **Graceful demotion, not silent failure.** When validation catches a problem, the response is proportional: schema errors prevent loading entirely, business rule violations (missing assets, broken graph) demote the task to `draft` status and log a clear warning. The rest of the system continues operating — one broken cartridge doesn't take down the registry (Framework Principle 11).

### 21. Live Session Integrity (The Sacred Brick)
*Motto: "A student mid-task is a promise we made. Don't break it."*

A live session is a student in a classroom, mid-task, engaged with the Trickster. That session is the atomic unit of the platform's purpose — every system exists to serve it. When definitions change around a live session — content reloads, prompts update, roadmaps restructure, rubrics evolve — the session must not break, corrupt, or produce undefined behaviour. The student doesn't know or care that the system changed underneath them. They're in the middle of learning.
- **Stale references are detected, not ignored.** When a session references a phase, task, prompt, or sequence that no longer exists in the current version, the system detects the mismatch explicitly. A `KeyError` in production is a broken promise. Every reference from session state to system definitions must have a staleness check.
- **Graceful recovery over silent corruption.** When a stale reference is detected, the system recovers proportionally: restart the task attempt from the new version, serve the last-known-good state, or present a clear message to the student. Never silently serve partial or inconsistent state — a student scored against a rubric that changed mid-task is worse than a student who gets asked to restart.
- **Session context survives transitions.** When a session crosses a boundary — static phase to AI phase, task to reveal, task to next task, prompt v1.2 to prompt v1.3 — the receiving side must inherit full relevant context. Exchange history, choices made, investigation paths taken, evaluation state. Silent context loss produces hallucination at best and unfair evaluation at worst (Framework Principle 19).
- **Changes are atomic from the session's perspective.** A reload, a deprecation, a prompt update — these happen between sessions or between task attempts, never mid-interaction. If the system can't guarantee atomicity (e.g., a long AI conversation spans a reload), it must detect and handle the boundary, not pretend it didn't happen.
- **Every mutable definition has a session impact analysis.** When designing a reloadable, updatable, or deprecatable resource (cartridges, prompts, roadmaps, rubrics, taxonomy configs), the vision and plan must specify: what happens to sessions that are currently using the old version? If the answer isn't documented, it hasn't been thought through.

---

## Review Checklist

When reviewing a vision document, phase plan, or implementation, use these questions:

### Safety & Ethics
- Does this feature respect the student? Would a 15-year-old feel respected or surveilled?
- Is any student data stored beyond what's needed? Can it be deleted?
- Does the Trickster reveal everything it did? Is there hidden manipulation that isn't explained?
- Is the content evergreen? Will it look dated or inappropriate in 2 years?

### AI Justification
- Does this feature need AI? Would static branching work just as well?
- Is the AI responding to what this specific student said and did?
- What happens if the AI fails? Is there a fallback?
- What's the token cost per student? Is the model choice justified?
- Does AI output pass through a safety check before reaching the student? What happens if the model generates something outside content boundaries?

### Team Handoff
- Can the team modify this without AI expertise?
- Are prompts in plain Markdown? Is the model swappable?
- Is the rationale documented, not just the structure?
- Are stubs and hooks clearly marked?

### Student Experience
- Does this keep the student engaged? Is there a dead zone where they get stuck with no guidance?
- Is this accessible in a browser? With a screen reader? In Lithuanian?
- Does the difficulty adapt to the student, or is it one-size-fits-all?

### Security
- Can a student's freeform input reach the AI without sanitisation? What's the prompt injection surface?
- Is tenant isolation enforced at the data layer? Could a crafted request leak cross-school data?
- Does this endpoint enforce role-based access, or does it trust the frontend?
- Do error responses leak internal details (paths, model names, stack traces)?
- Are there rate limits on AI-consuming endpoints?
- Do all database queries use parameterised statements? Does any user input reach a query without going through the data layer?

### Scale & Cost
- What happens at 800 schools? Does this scale horizontally?
- What's the AI cost per student? Is there a cheaper model that would work?
- Is there a static alternative for budget-constrained deployments?

### Modularity & Maintainability
- Can a new content type, trigger, or interaction be added without a code change?
- Are data formats using open type patterns, or are they gated on closed enums that require schema migration?
- If this component is removed or deprecated, do dependent systems handle it gracefully?
- Can content be updated without restarting the server?
- Is the rationale documented — not just what it does, but why it's built this way?
- Could a new team member understand and modify this component from the documentation alone?

### End-to-End Testing
- Is there a test that walks the full user journey for this feature — not just the component in isolation?
- Does the test use real data (reference cartridges, actual API calls), or synthetic fixtures that might hide integration failures?
- Are failure paths tested? What happens when AI fails, sessions expire, or referenced data is missing?
- Does the test hit the API boundary (like a real frontend would), or only internal functions?

### AI Experience (AX)
- Are AI-consumed interfaces (cartridge fields, rubrics, prompt structures) unambiguous? Could a field be misinterpreted?
- Do AI tools and endpoints return clear success/failure signals, or could the AI mistake a failure for an empty success?
- Is the AI's behaviour tested end-to-end — not just "did it receive the right input" but "did it produce correct output given this cartridge/rubric"?
- Are error messages actionable for content authors, or do they only make sense to developers?
- If cartridge content is injected into prompts, is the assembled result tested for correctness?
- Is every fact shown to the student derived from structured data, or is the AI trusted to generate facts it could hallucinate?
- When data crosses a system boundary (static → AI, session → evaluation, query → Composer), does the receiving system inherit full context? Could silent context loss cause wrong behaviour?

### Boundary Validation
- Is every resource (asset, prompt file, referenced task) validated for existence at load time — or could a student hit a 404 at runtime?
- Are structural constraints (phase graph reachability, terminal phases, bounded cycles) enforced at load time?
- When an identifier appears in multiple places, is consistency enforced at the boundary?
- Are file paths validated against directory traversal and unsafe characters before entering the system?
- When validation fails, does the system degrade gracefully (demote to draft, log clearly) — or fail silently or catastrophically?

### Live Session Integrity
- If this resource (cartridge, prompt, roadmap, rubric) is reloaded or updated, what happens to sessions currently using the old version?
- Can a student hit a stale reference (missing phase, deprecated task, changed rubric) mid-session? How is it detected?
- When a session crosses a system boundary (static → AI, task → reveal, prompt version change), does the receiving side inherit full context?
- Are changes atomic from the session's perspective — or could a mid-interaction reload produce inconsistent state?
- Is the session impact analysis documented in the vision/plan, or is it left as an implementation afterthought?

---

*Framework version: 1.8*
*Created: 2026-02-18*
*Updated: 2026-02-26 (Principle 12: streaming safety — redact pattern; Principle 19: tool calls for AI-to-platform signals)*
*Scope: Makaronas platform (all visions, all phases)*

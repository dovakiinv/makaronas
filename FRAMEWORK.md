# The Makaronas Framework
*Engineering Principles for an Educational AI Platform*

## Purpose

This framework establishes the design and engineering principles for the Makaronas platform. It is the lens through which every vision document, phase plan, and implementation decision is reviewed.

Makaronas is not a generic web app. It is an educational tool that uses AI to teach teenagers about media manipulation. The students are minors. The AI is adversarial by design. The content touches sensitive topics. Every principle here exists to ensure we build something that is **safe, effective, honest, and maintainable** — in that order.

---

## Scope

### What We're Building
An interactive platform where AI-driven adversarial dialogue teaches students to recognise media manipulation — headlines, cherry-picked citations, fabricated quotes, structural bias, social engineering, and the psychological triggers that make all of these work.

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

Every feature, every task, every AI interaction serves one purpose: teaching students to pause before reacting. Not to distrust everything — to think before they act.
- **Experience over lecture.** Students learn by being tricked, not by being told what tricks look like.
- **Instinct over knowledge.** The goal is a trained reflex, not a memorised list of manipulation techniques.
- **Growth over scores.** No points, no grades, no leaderboards. The platform tracks patterns and growth, not performance.

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
*Motto: "AI earns its cost by responding to what this student actually said and did."*

AI is not used for novelty. It's used where it's irreplaceable — where static content can't do the job.
- **Adversarial conversation.** AI pushes back on student skepticism: "What specifically? The source is real." Static branching can't do this.
- **Guided discovery.** AI narrows the search when a student is stuck, pointing them toward what to look for without giving the answer.
- **The mirror across tasks.** AI holds student history and confronts them with their own patterns across sessions.
- **Adaptive targeting.** AI shifts the attack vector to each student's specific vulnerability.
- **The empathy flip.** AI evaluates when students try to create manipulation themselves.
- **Calibrated judgment.** Some tasks have no manipulation. AI detects when students falsely accuse legitimate content.
- **The litmus test.** For every AI-driven feature, ask: "Would a static branching path work just as well?" If yes, make it static. AI is reserved for where it's irreplaceable.

### 7. The Dual Literacy (Platform as Teacher)
*Motto: "The platform IS the AI literacy lesson."*

The platform teaches both information literacy and AI literacy — not as separate modules, but through its own existence.
- **Students experience AI manipulation firsthand.** The Trickster is an AI. It tells them so. The lesson is: a machine just did this to you, and it can do it to millions simultaneously.
- **Teachers experience AI collaboration.** The Composer shows its reasoning, accepts overrides, explains its choices. It models what healthy human-AI interaction looks like.
- **The fourth wall break.** At key moments, the Trickster drops character entirely and speaks as an AI about what AI can do. This is the deepest teaching moment.

### 8. Team Accessibility (The Handoff Rule)
*Motto: "If the team can't change it without calling Vinga, it's not done."*

The platform will be maintained by a technical team without a dedicated AI specialist. Everything must be accessible.
- **Prompts are plain Markdown.** No special syntax, no code. The team opens a file, reads it, edits it. Git tracks the changes.
- **Model swapping is one line.** Change the model ID in `models.py`, optionally write a model-specific prompt file. Done.
- **Architecture is documented with rationale.** Not just "what" but "why." Future maintainers need to understand the reasoning behind decisions, not just follow instructions.
- **Hooks are clearly marked.** Every stub says what it does, what replaces it, and what interface to satisfy.
- **AI complexity is encapsulated.** The context management layer (layering, budgeting, prioritisation) is Vinga's domain, but it's documented well enough for a competent developer to debug and modify.

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
- **Localisation-ready.** Lithuanian is the primary language. Latvian and English are planned. The architecture supports language packs from day one without retrofitting.
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

---

*Framework version: 1.1*
*Created: 2026-02-18*
*Scope: Makaronas platform (all visions, all phases)*

# Task Roadmap

*Prioritised task development plan for the 5-school trial.*

**Session constraint:** ~30 minutes active platform time per lesson (Lithuanian class = 45 min, 10-15 min for discussion). Each task targets 5-10 minutes depending on depth.

**Model decision:** Upgrade from Flash Lite to Flash for trial tasks. Team feedback (Contento brainstorm §7) confirms Flash Lite produces confusion about what the AI wants — Flash's instruction-following and multi-turn coherence should resolve this.

---

## Priority 1: Refine Existing

### Investigation — "Sek pinigus" (Follow the Money)
- **Status:** Cartridge complete, needs UX refinement
- **Path:** `content/tasks/task-follow-money-001/`
- **Type:** Hybrid (static investigation tree → AI evaluation)
- **What works:** Strong content — two articles, financial chains, dead ends. The "follow the money" lesson is powerful.
- **What needs work:**
  - Team feedback (brainstorm §7.6): investigation tree UI is "mandrai gudrus" but unclear what it wants from the student
  - Need to clarify the student's goal at each step — what are they looking for, what constitutes a useful finding
  - Trickster evaluation phase needs testing on Flash (currently set to `standard` tier)
  - Consider reducing scope if 20 minutes is too long for a session slot
- **Task:** Refine UX, test on Flash, validate with a walkthrough

---

## Priority 2: Four New Archetype Tasks

Build in this order — each teaches a different medium and manipulation pattern:

### 1. Adversarial Dialogue — Fake Article (Tunguska-style)
- **Medium:** Article
- **Technique:** Emotional framing, cherry-picking, false authority
- **Interaction:** Paragraph-by-paragraph analysis with Trickster dialogue
- **Concept:** Student reads a sensational article with a compelling narrative. Embedded manipulation tactics (correlation=causation, slippery slope, bandwagon). Trickster defends the article's claims, student must identify specific manipulation techniques.
- **Team brainstorm:** Užduotis 1 — Tunguska article exists as content prototype
- **Teaching moment:** Summaries hide important context. Reading the full source reveals a different reality.
- **Design note:** The "read summary vs full article" choice isn't interesting as a gate — any student knows the teaching material wants them to read fully. Consider making the summary the *setup* (student reads summary first, forms opinion) and the full article the *investigation* (now find what the summary hid). The Trickster then challenges: "But the summary was accurate, wasn't it?"
- **Anti-shortcut:** Trickster must detect students who paste entire article back without identifying specific manipulation points. Push back: "You've shown me everything — but what *specifically* made you suspicious?"

### 2. Comment/Bot Analysis — Social Media Comments
- **Medium:** Social post (comment section)
- **Technique:** Ad hominem, whataboutism, mockery, emotional manipulation, coordinated amplification
- **Interaction:** Per-comment classification (who's writing: Bot/Troll/Normal/Unclear + what tactic they're using)
- **Concept:** Student sees an article excerpt, then comments appear one by one (simulating real chat). For each comment, student identifies the author type and manipulation tactic. Immediate feedback after each choice.
- **Team brainstorm:** Užduotis 2 — strong mockups with 5 comment profiles (Tiesos_Tarnautojas99, Jurgita_K, DebilasLietuvoje, Patriotas_Vytautas, Lietuvis_Tikras2024)
- **Teaching moment:** Bots spread emotions, repeat phrases, attack other commenters, derail discussion. Using tactics doesn't automatically mean bot — but it increases suspicion.
- **Real-world anchor:** BRELL energy grid bot campaigns in Baltic states (2022-2023), coordinated accounts with same phrases across languages.
- **Design note:** Team's mockup (brainstorm p4-5) is excellent — green/red immediate feedback with explanation. This maps to button interaction with instant reveal per comment.

### 3. Deepfake Awareness — Video Comparison
- **Medium:** Video
- **Technique:** Fabrication (AI-generated content)
- **Interaction:** Choice (which video is fake?) → reveal (both are fake)
- **Concept:** Two short video clips of the "same person" making different statements. Student asked: which is the deepfake? The reveal: **both are AI-generated.** Then progression: show AI video quality from 2 years ago → today → extrapolate tomorrow. The lesson isn't "spot the fake" — it's "you *can't* spot the fake, so what do you check instead?"
- **Teaching moment:** AI detection is a losing arms race. The real skills are: who uploaded it, is it on official channels, is there independent verification, does the source check out?
- **Design note:** This task requires pre-generated video assets. Keep it simple — two short clips (10-15 seconds each). The AI's role is in the post-reveal discussion, not the detection phase.
- **Real-world anchor:** 2022 Zelenskyy deepfake (Ukrainian president "ordering surrender"), quickly debunked through official channels.

### 4. Visual Manipulation — Image & Context Stripping
- **Medium:** Image
- **Technique:** Context stripping, misleading captioning, AI generation
- **Interaction:** Per-image analysis (which is AI-generated? which is real but miscontextualized? which is most dangerous for disinformation?)
- **Concept:** Three photographs with headlines about a fictional protest. One is fully AI-generated. One is a real photo from a different event with a false caption/date. One is a real photo of a person used as emotional manipulation (e.g., "mother who can't afford heating"). Student must determine which is which AND which is most dangerous.
- **Teaching moment:** A real photo in a false context is often MORE dangerous than an obvious fake — it's harder to debunk because the image itself is genuine. The most dangerous disinformation tool isn't fabrication — it's recontextualization.
- **Team brainstorm:** Užduotis 3 + real-world examples section (Pentagon explosion AI images, 2023)
- **Real-world anchor:** AI-generated Pentagon explosion images (2023) briefly crashed stock markets despite originating from a low-follower Twitter account.

---

## Priority 3: Additional Tasks (Post-Trial or Team-Authored)

These are strong concepts from Grok's brainstorm and team discussions. They can be built by the team using the archetype patterns established above, or prioritised for a second round.

### Coordinated Orchestra (Astroturfing)
- "The Great School Canteen Rebellion" — student analyses 10-12 coordinated fake posts
- Teaches: spotting coordination patterns (similar phrasing, timing, account age)
- Real-world: BRELL energy grid campaigns

### Whataboutism Duel
- Interactive role-play — AI plays the troll, student names the deflection tactic
- Teaches: recognising and resisting whataboutism in real-time
- Real-world: constant on Lithuanian history/NATO topics

### Victim Reversal
- "The New Language Rule at School" — sympathetic posts from "minority students"
- Teaches: how genuine sympathy is manufactured to flip narratives
- Real-world: Russian-speaker "oppression" framing in Baltic states

### Economic Doom Spiral
- "The New Phone Tax Disaster" — wave of posts about fictional teen-targeting law
- Teaches: fear-based manipulation targeting personal interests
- Real-world: BRELL grid "price explosion" campaigns

### Gradual Fear Escalation Feed
- "One Week in My Feed" — time-simulated feed that slowly escalates anxiety
- Teaches: recognising how mood is gamed through slow drip of content
- Real-world: NATO exercise escalation narratives

### Fake Grassroots Petition
- "Save Our Free Time!" — fake school petition with 200+ signatures
- Teaches: questioning whether "organic" movements are actually organic
- Real-world: fabricated petitions against defence spending

### Empathy Flip (from Makaronas archetypes)
- Student creates their own manipulation — AI evaluates their attempt
- Teaches: understanding the creator's perspective deepens recognition
- V5 engine fully supports this (context-isolated generation endpoint)

### Clean Check (from Makaronas archetypes)
- Legitimate content with no manipulation — student must recognise it's clean
- Teaches: discernment, not paranoia. Not everything is a trick.
- Engine supports inverted evaluation (`is_clean: true`)

---

## Teacher-Configurable Tasks (Post-Trial)

Team request: teachers want to use the same task *structure* with their own articles/content. E.g., the Tunguska rhetoric analysis task, but with a different article chosen by the teacher.

**What this means for task design now:**
- Trickster prompts should reference "the article" generically, not by specific content (e.g., "defend the claims in this article" not "defend the Tesla-Tunguska connection")
- Evaluation patterns should be described in terms of technique type ("emotional language", "rhetorical questions") not specific instances ("the Tesla paragraph")
- The cartridge format already supports this — article text is a presentation block, patterns are data. Swapping content is a JSON edit.

**What this means for the platform later:**
- A teacher-facing "create task from template" flow (simplified V8/Composer scope)
- Template cartridges with placeholder content blocks
- Validation that teacher-supplied content meets safety boundaries
- This is post-trial — but designing prompts generically now avoids a rewrite later.

## Open Questions

1. **Funder alignment** — Has the "AI content detection" framing been dropped? Does "workshops" mean facilitated group sessions or in-class individual work? Are older adults still in scope? *(Questions sent to team 2026-03-21)*
2. **Session bundling** — How does a teacher define a "session" (bundle of 3-4 tasks for one lesson)? This affects V6 evaluation design.
3. **Scoring/gamification** — Worth exploring for engagement. Achievements for engagement patterns ("you questioned a source 3 times") rather than correctness. Duolingo-style motivation without grading. Deferred to post-archetype.
4. **Model tier for trial** — Confirm Flash (standard) for all AI-driven tasks. Flash Lite (fast) remains available for simple evaluation-only tasks if needed.

---

*Last updated: 2026-03-21*

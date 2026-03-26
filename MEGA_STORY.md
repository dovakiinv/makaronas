# Mega Story — Game Design Direction

*"Pelican Brief meets Erin Brockovich meets All the President's Men meets Cyberpunk 2077"*

## The Vision (Full Game — Post-MVP)

An investigative journalism game where the student plays a junior reporter uncovering a massive corruption network. 60+ tasks across text, social media, images, video, and audio — each teaching a different media literacy skill, every discovery connecting to the same web.

The mega-corporation (working name: "Intelektas+" / "AteitisTech" / TBD) is manipulating Lithuania's education system — using bot farms, fake news portals, doctored images, and deepfakes to destroy public trust so they can sell their proprietary AI system as the "solution."

The game wrapper allows full dramatic stakes — framed teachers, deepfake confessions, coordinated city-vs-city campaigns — because it's a game. The emotional distance makes the learning deeper, not shallower. Students *forget* they're in a lesson. That's the point.

### Characters

- **The Student** — junior investigative journalist at a student media collective
- **Makaronas** — your editor. Sardonic, impatient, pushes you to dig deeper and verify everything. "Sakai nekaltas? Įrodyk." The Trickster teacher who makes you earn every conclusion.
- **The Network** — the adversary. Not a single villain but an ecosystem: shell companies, NGOs, bot farms, PR firms, all tracing back to the mega-corp. Each task peels back another layer.

### Progression

Each task teaches a skill through a different medium. Discoveries compound — what you learn in Task 1 (source checking) becomes a tool you need in Task 15 (when the sources are better disguised). The manipulation *evolves* as the student gets better — Makaronas adapts difficulty based on what the student has demonstrated.

---

## MVP Mini-Story: "The Fall of Teacher Vaitkus"

**Setting:** Panevėžys. A popular young IT/Math teacher at a gymnasium.

**The Incident:** A scandal breaks — Teacher Vaitkus is accused of selling exam answers on Telegram. It's everywhere. But something doesn't add up.

**Why this works for 16-18 year olds:**
- Every student has a favourite teacher. The emotional hook is immediate.
- Exams (brandos egzaminai, tarpiniai patikrinimai) are the highest-stakes thing in their lives.
- It's personal but not traumatic — investigative distance with emotional investment.
- The "who benefits?" revelation (tech corp wants to replace teachers with AI) is satisfying and complete in 4 tasks.

### Task Flow

**TASK 1: Two Headlines (Text Analysis)**
- Article A (sensationalist): "Panevėžys Teacher Caught Red-Handed Selling Exam Answers!"
- Article B (local blog): "Teacher Vaitkus Suspended Amidst Unverified Anonymous Claims"
- Makaronas: "Du straipsniai. Tas pats mokytojas. Visiškai skirtinga istorija. Kodėl?"
- Student investigates funding → Article A's portal is funded by shell NGO "Skaidri Ateitis"
- **Skill taught:** Source analysis, framing identification, financial trail following
- **Discovery:** Who is "Skaidri Ateitis"?

**TASK 2: Comment Section (Social Analysis)**
- Article A is posted to Facebook/Discord. Comments are a warzone.
- "Concerned citizens" demanding police intervention, students defending Vaitkus
- Makaronas: "90% pyksta. Bet ar visi tikri?"
- Student identifies bot patterns: new accounts, identical phrasing, coordinated timing
- **Skill taught:** Bot detection, coordinated inauthentic behaviour, genuine vs manufactured outrage
- **Discovery:** Bot accounts trace back to the same NGO from Task 1

**TASK 3: Images (Visual Analysis)**
- A "smoking gun" photo drops: Vaitkus in a dark alley handing an envelope to a student
- Makaronas: "Nuotrauka verta tūkstančio žodžių. Bet ar ji tikra?"
- Student finds AI artifacts (weird fingers, garbled text) OR reverse-image-searches to find the original (a brightly lit graduation photo, darkened and manipulated)
- **Skill taught:** AI image detection, context stripping, reverse image search, metadata analysis
- **Discovery:** The manipulated image's metadata contains a digital signature from a proprietary AI tool

**TASK 4: Video (Deepfake Awareness)**
- A "leaked" TikTok: Vaitkus in his car "confessing" to selling exams
- Makaronas: "Video! Negalima suklastoti prisipažinimo. Ar ne?"
- AI detection tools return "inconclusive" — teaching that tools aren't enough
- Student must verify the source, check timeline, find the original audio (a podcast where Vaitkus was quoting a book about corruption)
- **Skill taught:** Deepfake awareness, source verification over pixel analysis, audio forensics
- **Discovery:** The voice-cloning software belongs to a tech company. That company's primary funder? The same NGO "Skaidri Ateitis." The NGO is funded by "Intelektas+" — a tech corp pushing to replace teachers with AI.

**MVP Ending:** The student realizes this isn't about one teacher. It's a coordinated campaign to destroy trust in the education system so a corporation can sell the "solution." Makaronas: "Dabar matai visą grandinę. Bet tai tik pradžia."

---

## Design Principles

- **Game first, lesson second.** If it feels like homework, we failed.
- **The corruption IS the curriculum.** Each manipulation technique is taught by encountering it in the wild, not by reading about it.
- **Skills compound.** What you learn in Task 1 becomes a tool for Task 15.
- **Makaronas evolves.** As the student demonstrates skills, Makaronas pushes harder and trusts more.
- **The network evolves.** If the student easily spotted bots by account age in Task 2, later tasks use aged accounts with stolen profile photos.
- **Real Lithuanian context.** Towns, schools, exams, cultural references — this is THEIR world, not a generic "media literacy" abstraction.

---

## Relationship to Current Architecture

The cartridge system, AI engine, and evaluation framework all support this direction:
- Each task is a cartridge with presentation blocks (articles, comments, images, video)
- Makaronas as editor = narrator persona mode (already built)
- Discovery connections between tasks = session-level context (V6 territory)
- Skill progression = cross-task evaluation patterns (V6 territory)
- Teacher-configurable tasks = template cartridges with swappable content (post-trial)

The Glitch Protocol UI from the Stitch experiments maps perfectly to this game aesthetic.

---

*Written: 2026-03-25*
*Status: Direction agreed with team. MVP = Teacher Vaitkus, 4 tasks.*

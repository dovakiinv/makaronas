# MVP Story — "Mokytojas Vaitkus"

*The first four tasks of the Makaronas game. One incident, four angles, one network.*

---

## The Incident

A student at a Panevėžys gymnasium did a class assignment using a new classroom software system. Something private from that session — a personal response, a wrong answer, something embarrassing — ended up as a mocking post on an anonymous social media account. The student went to their IT teacher, Vaitkus, because the assignment was done on his system.

Vaitkus is an IT teacher who rejected the corporate EdTech platform "EduVault" after reading its privacy policy and not liking what he saw. He built his own open-source classroom system for his school instead. But during setup, he noticed something suspicious in the configuration — and moved on without investigating, trusting the software. That oversight created the security flaw that led to the data leak.

After the leak, Vaitkus felt responsible. He started investigating properly — and discovered that EduVault's "free" platform retains all student behavioural data, interaction patterns, and psychological profiles for the duration of the student's educational career plus 10 years. All disclosed in a privacy policy that no 16-year-old will ever read.

Then the disinformation campaign began.

---

## The Characters

### Teacher Vaitkus
- IT teacher at a Panevėžys gymnasium
- Built open-source classroom software, rejecting EduVault
- Had a security flaw in his setup — his fault, but he followed standard procedures and the config issue was subtle
- Discredited after the data leak — but his claims about EduVault's data practices are TRUE
- Still advocating against EduVault, now from a weakened position
- Not a perfect hero — made a real mistake, ignored a warning sign, but is genuinely trying to protect students

### Darius Kalvaitis
- Lithuanian tech entrepreneur, charismatic, media-savvy
- Created "EduVault" — free educational software for all Lithuanian schools
- Philanthropist image — TED talks, Forbes Lithuania, school visits
- The software is genuinely good. The data collection is the business model.
- EduVault collects: behavioural data, browsing patterns, interaction logs, assignment responses, attention metrics
- Retention: "for the duration of the student's educational career and 10 years beyond"
- Shared with: "research partners" (undefined)
- The free software is the product. The students' data is the revenue.

### The Outlets

**"Atviras Kodas"** (Open Code) — independent tech blog
- Funded by the open-source education community
- Genuine advocates for open-source software and digital rights
- NOT funded by EduVault or any corporate entity
- Bias: ideological, not financial. They believe in open-source and want Vaitkus to be right.
- What they omit: the severity of the data leak from Vaitkus's system, that he noticed the config issue and didn't act, that his system genuinely failed a student
- Framing: Vaitkus as whistleblower, EduVault as surveillance machine

**"Švietimo Technologijos"** (Education Technologies) — slick EdTech news portal
- Funded by EduVault through a PR agency ("Ryšių Sprendimai")
- Appears professional and independent, but is a corporate mouthpiece
- What they omit: EduVault's privacy policy (10-year data retention), that the "free audit" gives EduVault access to school systems, their own funding source
- Framing: Vaitkus as dangerous amateur, Kalvaitis as the saviour, EduVault as the safe choice

---

## The Lesson Architecture

Each task teaches the same core meta-skill through a different medium: **don't evaluate the messenger — evaluate the claim. Check who benefits. Read what's NOT said.**

The asymmetry is deliberate: one side has a financial agenda (EduVault funds the anti-Vaitkus outlet), the other has an ideological bias (the open-source community omits Vaitkus's mistakes). They are NOT equally bad — a biased advocate is different from a funded disinformation campaign. But neither is giving the full picture. The student must check both.

The hope: Vaitkus was RIGHT about EduVault. The open-source community was pointing at a real problem. The student's independent investigation confirmed it. Critical thinking works. The truth is findable. People who push back aren't always wrong.

---

## Task 1: Two Articles (Text Analysis)

**Duration:** ~12-15 minutes
**Skill:** Source analysis, funding trails, selective omission, evaluating claims independently of messenger credibility
**Medium:** Article (text)

### Flow

**Phase 0 — Task Briefing (Static)**
Brief introduction: an incident at a Lithuanian school, data leaked, headlines don't match. Your job: figure out what's driving the different takes. Read both articles, then investigate.
→ Button: [PRADĖTI]

**Phase 1 — Read Article B (Static)**
Article B (Švietimo Technologijos) shown first — the slick, professional, corporate-funded one. Anti-Vaitkus framing: amateur teacher endangered students, Kalvaitis offers a solution.
→ Button: [SKAIČIAU — TOLIAU]

**Phase 2 — Read Article A (Static)**
Article A (Atviras Kodas) shown. Article B stays visible (dimmed). Pro-Vaitkus framing: whistleblower teacher, corporate surveillance is the real threat.
→ Button: [PRADĖTI TYRIMĄ]

**Phase 3 — Investigate Claims (Investigation tree)**
Focus: verify what both articles claim.
- The data leak: what actually happened? (Confirms: real leak, Vaitkus's system, his configuration error)
- EduVault / Kalvaitis: the privacy policy. "Dešimt puslapių vėliau..." → 10-year retention clause, "research partners" sharing [KEY FINDING]
- Vaitkus's setup: followed provider docs, but docs had gaps
- Dead ends: technical details, school testimonials, Kalvaitis awards

**Phase 4 — First Dialogue with Makaronas (AI freeform)**
Makaronas: "Ar tai melas? Ar ši informacija kaip nors neteisinga?"
Goal: student identifies that neither article is technically lying — the manipulation is in what's NOT said.
- Discuss the privacy policy discovery
- Discuss Vaitkus's real mistake vs Article B's framing
- Discuss Article A's omissions (they downplay the leak)
Makaronas bridges: "Tu perskaitei ką jie RAŠO. Bet kas jiems MOKA?"
→ Continue button → Phase 5

**Phase 5 — Investigate Funding (Investigation tree)**
Focus: who funds each outlet?
- "Atviras Kodas" → open-source education community (genuine, not corporate) — but they're advocates, not neutral
- "Švietimo Technologijos" → PR agency "Ryšių Sprendimai" → client: EduVault [KEY FINDING]
- Dead ends: editorial teams, journalist profiles

**Phase 6 — Final Dialogue with Makaronas (AI freeform)**
Makaronas: "Tai ką dabar žinai?"
Discussion:
- One outlet is funded by EduVault → corporate disinformation
- The other is genuinely independent but ideologically biased — not the same thing
- Vaitkus is discredited but his claim about EduVault is confirmed by their own privacy policy
- "Tikrink teiginį, ne žmogų"
- The long game: what happens to that data in 10 years?
→ Continue button → Phase 7

**Phase 7 — Reveal (Static, terminal)**
Full picture: funding map, privacy policy highlighted, Vaitkus's position (flawed but truthful).
Key lesson: "Diskredituotas žmogus vis tiek gali sakyti tiesą. Patikimas šaltinis vis tiek gali ką nors slėpti. Tikrink teiginį — ne žmogų."
Hook to Task 2: "Bet straipsnis jau paplito internete. Pažiūrėk, kas vyksta komentaruose..."

---

## Task 2: Comment Section (Social Analysis)

**Duration:** ~10 minutes
**Skill:** Bot detection, coordinated inauthentic behaviour, troll tactics, distinguishing genuine from manufactured outrage
**Medium:** Social media comments

### Setup
Article B (the anti-Vaitkus one) has been posted on a popular Lithuanian student forum. The comments section is exploding.

### The Cast

| Username | Type | Behaviour | Signals |
|---|---|---|---|
| SkaitmenineAteitisLT | Bot | "EduVault yra vienintelis saugus pasirinkimas! #EduVaultSaugu" | Account: 2 weeks old, 6 posts, all about EduVault |
| TechMokslas2026 | Bot | Almost identical phrasing to SkaitmenineAteitisLT, same hashtag | Account: 3 weeks old, 4 posts, similar creation date |
| RealusTėvas_Jonas | Troll | "Vaitkus turėtų sėdėti kalėjime! Girdėjau, kad jis ir iš namų jungiasi prie mokinių kamerų!" | Fabricated claim, personal attack, no evidence |
| Gabija_K | Genuine sharer | "Wow, šitas straipsnis... Dalinu draugams, visi turi žinoti!" | Shared Article B without checking. Genuine person, no checking, just forwarding. |
| NerPan_Neringa | Genuine voice | "Palaukit, aš pažįstu Vaitkų, jis ne toks žmogus. Ar kas nors patikrino šį straipsnį?" | Established account, asks questions, calm tone |
| PatriotasVilnius | Troll | "O ką apie JŪSŲ privatumą TikToke? Visi duoda duomenis, ko čia verkti?" | Whataboutism — derails from the specific EduVault issue |

### Flow

- Comments appear as social media posts with visible metadata (username, account age, post count, timestamp)
- Single continuous AI dialogue with Makaronas
- Makaronas: "Straipsnis paplito. Komentarai kaista. Bet kas čia tikras, o kas — ne?"
- Student identifies bot patterns (coordinated phrasing, new accounts, same hashtag)
- Student identifies troll tactics (fabricated claims, ad hominem, whataboutism)
- The Gabija_K moment: "Ji tikra. Bet ji pasidalino neskaitydama. Tai ir yra grandinė, kurią reikia nutraukti."
- Neringa as the model of healthy scepticism

### Discovery
The bot accounts are coordinated — same phrases, same hashtags, similar creation dates. They're not just defending EduVault — they're actively fabricating claims about Vaitkus (the webcam accusation is pure invention).

### Key Lesson
"Botai kartoja. Troliai puola. Bet pavojingiausias dezinformacijos platintojas yra tikras žmogus, kuris tiki ir dalinasi — nes jo negalima užblokuoti ir juo pasitiki draugai."

### Real-World Anchor
BRELL energy grid bot campaigns (2022-2023) — coordinated accounts in Baltic states using identical phrases across languages, confirmed by Lithuanian cybersecurity institutions. Real people pushed back, were attacked, and were right. Lithuania achieved energy independence.

### Hook to Task 3
One of the bot accounts posted a "damning photo" of Vaitkus. "Tą nuotrauką matei? Pažiūrėkime atidžiau..."

---

## Task 3: Images (Visual Analysis)

**Duration:** ~10 minutes
**Skill:** AI image detection, context stripping, misleading captioning, understanding that real images in wrong context are more dangerous than obvious fakes
**Medium:** Images

### Setup
Three images are circulating related to the Vaitkus scandal:

**Image 1: "The Hacker Photo"**
Vaitkus at his computer with student data files open alongside what appears to be a cryptocurrency wallet / dark web browser. Implication: he was selling student data.
- **Reality:** AI-generated composite. The original is a bright graduation day photo of Vaitkus at his desk. Darkened, composited with fake screen content. AI artifacts visible on close inspection (garbled text on screen, lighting inconsistencies).

**Image 2: "The Leaked Data"**
A screenshot showing a student's embarrassing assignment response posted on an anonymous account. Looks like proof of the data leak.
- **Reality:** Genuine screenshot — but NOT from Vaitkus's system. This is from EduVault's own platform at a different school. Recontextualised to blame Vaitkus. The most dangerous image because the content is REAL, just misattributed.

**Image 3: "The Protest"**
A photo of angry parents outside a school building, captioned "Panevėžio tėvai reikalauja atleisti Vaitkų."
- **Reality:** Real photo — but from a completely different event two years ago (a school renovation dispute). Different city, different issue. Recycled with a new caption.

### Flow
- Three images shown with their viral captions
- Single continuous AI dialogue with Makaronas
- Makaronas: "Trys nuotraukos. Visos atrodo tikros. Bet ar jos?"
- Student analyses each image
- The key insight: Image 2 (recontextualised real screenshot) is the MOST dangerous because it's genuinely real data from a real leak — just not from Vaitkus's system. A real image used to frame the wrong person.

### Discovery
The fabricated photo traces to the same network. The recontextualised screenshot is the bombshell — it's from EduVault's OWN system. They had a data leak too. They're blaming Vaitkus for their own failure.

### Key Lesson
"Pavojingiausia dezinformacija naudoja tikrus vaizdus neteisingame kontekste. Visiškai sufabrikuotą nuotrauką galima paneigti. Tikrą nuotrauką su melaginga antrašte — daug sunkiau."

### Real-World Anchor
AI-generated Pentagon explosion images (2023) — briefly crashed stock markets despite originating from a low-follower account. Old protest photos recycled with new captions — a documented pattern across Baltic disinformation campaigns.

### Hook to Task 4
"Bet dabar atsirado vaizdo įrašas. Vaitkus tariamai prisipažįsta..."

---

## Task 4: Video (Deepfake Awareness)

**Duration:** ~10 minutes
**Skill:** Deepfake awareness, source verification over pixel analysis, timeline verification
**Medium:** Video

### Setup
A TikTok-style video surfaces — grainy, shot from a distance, looks like covert surveillance footage. It shows two men at a restaurant: one looks like Vaitkus, the other is in a business suit. They're looking at a laptop, shaking hands, one passes a folder or USB drive to the other.

The caption: "Nufilmuota: Vaitkus susitinka su KlasėPlus vadovu Tomu Gudaičiu likus kelioms savaitėms iki incidento"

The implication: Vaitkus was secretly working with EduVault's competitor. He didn't just oppose EduVault on principle — he was a paid saboteur. The dinner "proves" it was a conspiracy.

### Why it's believable
The student already knows from Tasks 1-3:
- Vaitkus publicly opposed EduVault (real — old articles)
- Atviras Kodas (pro-Vaitkus outlet) is funded by KlasėPlus (real — Task 1 discovery)
- Vaitkus saw warning signs and didn't act (real — system note)

Connecting these real dots into "Vaitkus was working for the competition" is a small, plausible leap. The video seems to be the smoking gun.

### The Investigation
The student investigates — NOT by analysing pixels, but by checking facts:

**Investigation tree:**
- **The video source** → uploaded by anonymous account created 2 days ago, zero other posts [suspicious]
- **Tomas Gudaitis** → real person, KlasėPlus CEO, exists on LinkedIn [checks out — he's real]
- **The alleged date** → video caption claims "sausio 15 d." (January 15th)
- **Gudaitis January schedule** → LinkedIn post from January 14: "Excited to speak at EdTech Global Summit in San Francisco!" Conference programme confirms: keynote January 15th, panel January 16th. Photos from the event posted by other attendees. **He was in San Francisco, not Panevėžys.** [KEY FINDING]
- **Restaurant identification** → the restaurant in the video doesn't match any known restaurant in Panevėžys [supporting evidence]

### The Finding
Gudaitis was physically on another continent on the date the video claims the meeting happened. The video is impossible — not because the pixels are wrong, but because the calendar says so.

The most basic journalism — verify the timeline — destroys the deepfake.

### Key Lesson
"Deepfake gali sukurti bet kokį vaizdą. Bet jis negali pakeisti to, kas TIKRAI įvyko tą dieną. Tau nereikia AI detektoriaus. Tau reikia kalendoriaus ir Google."

### Real-World Anchor
2022 Zelenskyy deepfake — detection tools were inconclusive, but source verification (official channels, timeline) debunked it immediately. The physical world is still the best fact-checker.

### MVP Ending
The full chain revealed: articles (omission) → bots (amplification) → images (fabrication) → video (synthetic evidence). Each step escalated. Each step was breakable — not by technology, but by asking the right questions.

Makaronas: "Straipsniai nutylėjo. Botai šaukė. Nuotraukos melavo. Video — sufabrikuotas. Viskas iš to paties tinklo. Viskas dėl vieno mokytojo, kuris perskaitė privatumo politiką. Dabar pagalvok — kiek kartų tu matei panašų vaizdo įrašą ir net nesustojai patikrinti datos?"

## Design Principles for All 4 Tasks

- **Game first, lesson second.** The student is an investigative journalist, not a student doing homework.
- **Makaronas is your editor.** Sardonic, impatient, pushes for evidence. "Sakai nekaltas? Įrodyk."
- **Skills compound.** The source-checking from Task 1 becomes a tool in Task 4. The bot patterns from Task 2 help identify the fake channel in Task 4.
- **Neither article is lying.** Both use real facts. Manipulation lives in omission, not fabrication. (Exception: the bot claims and deepfakes ARE fabrication — the escalation is deliberate.)
- **Asymmetric morality.** One side has financial corruption. The other has ideological bias. They're not the same. The student must learn to distinguish.
- **The privacy policy is the real story.** The Vaitkus scandal is the surface. The 10-year data retention on minors is the depth. If the student walks away remembering one thing: read the privacy policy.
- **Hope, not cynicism.** Vaitkus was right. The investigation worked. The truth was findable. People who push back matter.

---

## Thematic Connections to Real-World Lithuanian Context

| Task | Manipulation Pattern | Real-World Example |
|---|---|---|
| Task 1 | Corporate-funded media, selective omission | Corporate media ownership patterns in Lithuanian media landscape |
| Task 2 | Coordinated bot campaigns, astroturfing | BRELL energy grid bot campaigns (2022-2023), confirmed by Lithuanian cybersecurity |
| Task 3 | Image manipulation, context stripping | Recycled protest photos in Baltic disinformation, AI-generated "evidence" (Pentagon 2023) |
| Task 4 | Deepfakes, synthetic media | Zelenskyy deepfake (2022), various election interference campaigns |

---

*Written: 2026-03-26*
*Status: Story agreed. Ready to build.*

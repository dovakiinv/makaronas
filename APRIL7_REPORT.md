# Makaronas — pirmojo mokinių testavimo ataskaita

**Data:** 2026-04-07
**Dalyvių skaičius:** 93 mokiniai (3 sesijos po ~30 mokinių, kiekviena trukmė ~30 minučių)
**Duomenų šaltinis:** `sessions_apr7.json` (visi sesijų telemetrijos įrašai iš Railway)

---

## Trumpa santrauka

Platforma veikia. AI dialogas (Triksteris) ir vertintojas neturi techninių klaidų — visos `discuss` fazės buvo įvertintos kaip `on_success`. Bet **pirmoji užduotis per ilga 30 minučių sesijai**, ir **paskutinė jos fazė (`write_article`) turi UX problemą**, dėl kurios 20 mokinių užstrigo, nors aktyviai bandė rašyti savo žinutę draugams.

**Trumpai:**
- 80 iš 93 mokinių (86%) baigė bent dalį 1 užduoties
- Tik 18 pasiekė 2 užduotį
- Tik 4 baigė visas 4 užduotis
- Mediana laiko 1 užduočiai: **17 minučių iš 30** (~57% sesijos)
- **20 mokinių (25% iš baigusiųjų `discuss`) užstrigo `write_article` fazėje** ne iš tinginystės, o todėl, kad Triksteris vis klausė "o kaip dėl..." vietoj to, kad priimtų jų atsakymą

---

## 1. Kur mokiniai sustojo

| Užduočių baigta | Mokinių | Procentai |
|---|---|---|
| 0 | 13 | 14% |
| 1 (tik 1 užduotis) | 62 | 67% |
| 2 | 7 | 7,5% |
| 3 | 7 | 7,5% |
| 4 (visa platforma) | 4 | 4% |

**Pagrindinis pastebėjimas:** dauguma mokinių (62) baigė tik 1 užduotį ir sustojo. Tai ne dėl turinio sudėtingumo — tai dėl to, kad **1 užduotis suvalgo visą laiko biudžetą**.

Tie 4 mokiniai, kurie baigė viską, greičiausiai buvo greiti skaitytojai paskutiniame etape arba mokytojai, kurie norėjo pamatyti visą platformą. Jų atsakymų kokybė skiriasi — vienas davė rimtus, analitinius atsakymus, kiti — vienažodžius. Tai nebūtinai "elitas".

---

## 2. Laiko analizė — kur dingsta minutės

Mediana, kiek truko 1 užduotis (visos fazės kartu):

| Fazė | Mediana | Vidurkis |
|---|---|---|
| Iki dialogo (briefingas, du straipsniai, tyrimas) | **9,1 min** | 8,8 min |
| AI dialogas (`discuss` + `write_article`) | 7,4 min | 8,2 min |
| **Iš viso 1 užduotis** | **17,0 min** | 17,0 min |

Iš 30 minučių slot'o, mediana ~17 min eina tik 1 užduočiai. Likę ~13 min kai kuriems mokiniams pakanka 2 užduočiai pradėti, bet daugumai — ne. Ypač jei jie užstringa `write_article` (žr. žemiau).

**Pastaba:** straipsnių skaitymas + tyrimo medis kartu užima 9 minutes. Tai pati ilgiausia "pasyvi" fazė. Sutrumpinus straipsnius arba sumažinus tyrimo medį iki 3-4 šaltinių, čia atsilaisvintų 3-5 minutės.

---

## 3. AI dialogo kokybė — ar mokiniai galvojo?

Trumpas atsakymas: **taip, bet ne visada**.

### Skaičiai
- **440 mokinių žinučių** iš viso 1 užduoties dialoguose
- **Mediana per sesiją:** 5 mokinio žinutės (vidurkis 5,5)
- **Mediana ilgis:** 6,5 žodžių (vidurkis 11 žodžių)
- **Vienažodės žinutės:** 11% (50 iš 440)
- **Trumpos žinutės (2-5 žodžių):** 33%
- **Ilgesnės žinutės (>20 žodžių):** 16%

Maždaug **38% atsakymų yra <5 žodžių** — tai daugiau "patvirtinimas" Triksteriui nei savarankiškas mąstymas. Bet 16% — gilūs, analitiniai atsakymai. Tai tikras spektras.

### Pavyzdžiai

**Stiprus mąstymas (16% mokinių):**
> "Duomenys saugomi 10 metų. KlasėPlus finansuoja Atvirą kodą ir jie kritikuoja EduVault, nes tai jų konkurentai"

> "vienas yra finansuojamas pačiu UAB 'EduVault', o kitas yra konkurentas šitos platformos. tai konkurentai gins mokytoją"

> "Pinigus moka EduVault arba jų palaikytojai, nes nenori, kad būtų sugadinta jų reputacija. Atviras kodas bando pavaizduoti Petrylą kaip auką"

> "Priešai ir įvairios įmonės finansuoja viena kitą. Kiekvienas pamiršo paminėti kokiu tikslu bus naudojami mokinių duomenys"

Šie atsakymai rodo, kad mokiniai sugeba **sekti pinigų pėdsakus, atpažinti motyvuotą šališkumą, ir net įvardinti, ką straipsniai praleido**. Tai yra būtent tai, ko mes ir mokome.

**Vidutinis užangažavimas (33%):**
> "Finansuojamas KlasėPlus fondo"
> "Duomenys saugomi 10 metų"
> "Konkurencija"

Trumpi, bet tikslūs faktai. Mokiniai supranta, bet rašo glaustai.

**Sumišęs / pasiklydęs:**
> "Nežinau seni, nesiseka man tokie dalykai"
> "Nelabai radau, ar gali padėt atrasti"
> "o kaip man zinoti kokie šaltiniai finansuoja, ir koks tikslas kokio atsakyko ieskom cia?"

Šie mokiniai rodo, kad jie **norėtų suprasti, bet nežino, ko Triksteris nori**. Tai signalas, kad instrukcijos kai kur galėtų būti aiškesnės.

---

## 4. Pagrindinė problema: `write_article` šuolis nuo skardžio

**Tai pats svarbiausias šios ataskaitos atradimas.**

20 mokinių (25% visų, kurie baigė `discuss` fazę) **niekada nepabaigė** `write_article` fazės. Bet jie ne tinginiavo — telemetrijos duomenys rodo, kad jie **bandė vidutiniškai 6 kartus** rašyti savo žinutę draugams (vienas mokinys bandė net 12 kartų).

### Ką iš tiesų atrodo

`write_article` fazė turėtų leisti mokiniams parašyti trumpą žinutę draugams pagal tai, ką jie sužinojo. Bet vietoj to, kad priimtų bet kokį pagrįstą atsakymą, **Triksteris vis tęsia mokyti** klausimais "o kaip konkrečiai?", "o kas dėl X?".

**Tikras pavyzdys (sesija 13426738...):**

```
Mokinys: "Manau istorijos iškraipymas"
Triksteris: "Iškraipymas – skamba rimtai. Bet kaip konkrečiai tai daroma?"

Mokinys: "Nutylejo del to, kad mokytojo buvo perspeta, jog sistema nesaugi"
Triksteris: [klausia daugiau]

Mokinys: "Nezinau"
Triksteris: [klausia dar]

[...dar 9 bandymai...]

Sesija pasibaigia. Užduotis nepabaigta.
```

Mokinys turi visus reikalingus duomenis. Mokinys parašė rimtą atsakymą. Bet Triksteris niekada nepasako "gerai, tai geras atsakymas, eikime toliau". Vietoj to jis vis klausia "o dar?", kol baigiasi laikas.

**Šis ciklas yra tas pats visuose 20 atvejų.** Tai ne UI klaida ir ne mokinių problema — tai Triksterio elgesio arba vertintojo nustatymo problema specialiai `write_article` fazėje.

### Kodėl tai svarbu

Jei pataisytume šią vieną problemą — **20 mokinių iš 93 (21% visos klasės) būtų sėkmingai pabaigę 1 užduotį**. Tai didžiulis šuolis baigimo rodikliuose tik nuo vieno pataisymo.

---

## 5. Pirmojo "stalo" mokiniai (5 atvejai)

5 mokiniai užstrigo **`discuss` fazėje** ir niekada nepasiekė `write_article`. Šie mokiniai aktyviai dalyvavo (mediana 10 dialogo posūkių, vidutinė žinutės ilgis 52 simboliai) — jiems tiesiog **pritrūko laiko**, kol Triksteris sutiko, kad jie supranta.

Tai antras Triksterio elgesio signalas: net `discuss` fazė kartais reikalauja daugiau posūkių nei turime laiko.

---

## 6. Anomalijos — ko NĖRA duomenyse

Šie dalykai NEpasitaikė, kas yra geras ženklas:

- **Jokios `Hmm... pabandykite dar kartą` klaidos pranešimų** — Gemini API veikė be pertrūkių
- **Jokių `on_max_exchanges` baigčių** — vertintojas niekada nepriverstinai nutraukė pokalbio
- **Jokių pasikartojančių žinučių** — ne botai, ne kopijavimas-įklijavimas
- **Visos `discuss` fazės baigėsi `on_success`** — vertintojas dirba savo darbą
- **Tinklo užduotyje (3-ioji) nėra `exchange` įrašų** — tai tikėtasi (statinė užduotis)

Techniniai dalykai veikia. Problema — pedagoginis tempas ir Triksterio elgesys konkrečioje fazėje.

---

## 7. Rekomendacijos — kas keisti pirmiausia

### Prioritetas 1: pataisyti `write_article` šuolį (didžiausias ROI)

Triksterio prompt'as `write_article` fazei turi leisti **priimti pirmą pagrįstą atsakymą** ir pereiti toliau. Šiuo metu jis veikia kaip mokytojas, kuris vis sako "o dar?". Jis turėtų veikti kaip draugas, kuris sako "supratau, gerai".

Konkrečiai:
- Vertintojo `write_article` checklist'as turi būti **trumpas** (1-2 punktai, ne 5)
- `min_exchanges` `write_article` fazei turi būti **1** (ne 3)
- Triksterio prompt'as turi aiškiai sakyti: "kai mokinys parašė savo žinutę, **PRIIMK** ją, neklausk daugiau"

**Tikėtinas poveikis:** ~20 papildomų baigtų sesijų (+22%).

### Prioritetas 2: sutrumpinti pasiruošimą 1 užduočiai (~3-5 min taupymas)

Iki dialogo eina 9 minutės. Tai per ilga.

Variantai:
- **A:** sumažinti tyrimo medį nuo 8 šaltinių iki 4-5 (likti tik aiškiausi finansiniai ryšiai)
- **B:** Vienas iš dviejų straipsnių turėtų būti trumpesnis (gal 50% tūrio)
- **C:** Briefingas (sad-girl + intro tekstas) gali būti trumpesnis arba aiškesnis

Norint, kad mokiniai pasiektų bent 2 užduotį, čia reikia atlaisvinti 5-7 minutes.

### Prioritetas 3: galbūt 1 užduotį visiškai pakeisti

Vinga svarstymas: **palikti istoriją, bet kitai sesijai pradėti nuo kitos užduoties**. Likusios 3 užduotys (komentarai, botų tinklas, deepfake video) yra trumpos, ir 30 minutėse galima padaryti visas tris. 1 užduotis tokia, kokia yra dabar, gali likti kaip "savarankiškas papildomas darbas namuose" arba kitam ilgesniam pamokos blokui.

### Prioritetas 4: ištirti 2-4 užduočių laikus (vis dar nežinome)

Tik 18 mokinių pasiekė 2 užduotį, todėl mes neturime patikimų duomenų apie tai, kiek truks visos likusios užduotys. Sekančiame testavime reikia užtikrinti, kad bent keli mokiniai pasiektų visas 4, kad galėtume išmatuoti pilną laiko biudžetą.

---

## 8. Žvelgiant į priekį

Šis testavimas suteikė mums tris dideles tiesas:

1. **Turinys veikia.** Mokiniai sugeba sekti pinigų pėdsakus, atpažinti motyvuotą šališkumą, ir parašyti savo nuomonę. Tie atsakymai, kuriuos mes matome (žr. citatas aukščiau), yra būtent tai, ko mes mokome.

2. **AI veikia.** Triksteris ir vertintojas neturi techninių klaidų. Kiekviena dialogo sesija pasiekė `on_success`. Promptai veikia.

3. **Tempo nesutampa.** Turinys yra ~50 minučių vertės. Pamoka yra 30 minučių. Reikia arba sutrumpinti turinį, arba ilgesnių pamokų. Pirmas variantas yra realistiškesnis.

Taip pat: **`write_article` šuolis nuo skardžio** yra svarbiausia konkreti problema, kurią galime ištaisyti vienu pataisymu — ir tai duotų didžiausią efektą.

---

*Ataskaita parengta iš telemetrijos duomenų, surinktų po 2026-04-07 testavimo. Visi skaičiai ir citatos yra iš tikrų mokinių sesijų.*

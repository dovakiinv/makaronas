# Makaronas — pirmojo mokinių testavimo ataskaita

**Data:** 2026-04-07
**Dalyvių skaičius:** 93 mokiniai (3 sesijos po ~30 mokinių, kiekviena trukmė ~30 minučių)
**Duomenų šaltinis:** `sessions_apr7.json` (visi sesijų telemetrijos įrašai iš Railway)

---

## Trumpa santrauka

Platforma veikia. AI dialogas (Makaronas) ir vertintojas neturi techninių klaidų — visos `discuss` fazės buvo įvertintos kaip `on_success`. Bet **pirmoji užduotis per ilga 30 minučių sesijai**, ir **paskutinė jos fazė (`write_article`) turi UX problemą**, dėl kurios 20 mokinių užstrigo — pusė jų pritrūko laiko, kita pusė bandė rašyti, bet Makaronas reikalavo „sujungti viską į vieną žinutę", net kai studentai jau buvo padengę abu punktus per keletą atskirų atsakymų.

**Trumpai:**
- 80 iš 93 mokinių (86%) baigė bent dalį 1 užduoties
- Tik 18 pasiekė 2 užduotį
- Tik 4 baigė visas 4 užduotis
- Mediana laiko 1 užduočiai: **17 minučių iš 30** (~57% sesijos)
- **20 mokinių (25% iš baigusiųjų `discuss`) užstrigo `write_article` fazėje:**
  - **10 mokinių pritrūko laiko** — gavo Makarono raginimą rašyti, bet niekada nespėjo atsakyti arba tik vieną kartą
  - **10 mokinių bandė rašyti**, bet Makaronas atmetė jų atsakymus, nes reikalavo, kad **abu radiniai būtų vienoje žinutėje** — net jei mokiniai jau juos buvo paminėję per kelias atskiras žinutes

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

Maždaug **38% atsakymų yra <5 žodžių** — tai daugiau "patvirtinimas" Makaronui nei savarankiškas mąstymas. Bet 16% — gilūs, analitiniai atsakymai. Tai tikras spektras.

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

Šie mokiniai rodo, kad jie **norėtų suprasti, bet nežino, ko Makaronas nori**. Tai signalas, kad instrukcijos kai kur galėtų būti aiškesnės.

---

## 4. Pagrindinė problema: `write_article` šuolis nuo skardžio

**Tai pats svarbiausias šios ataskaitos atradimas.**

20 mokinių (25% visų, kurie baigė `discuss` fazę) niekada nepabaigė `write_article` fazės. Tai NĖRA mokinių apsileidimas — telemetrijos duomenys rodo, kad jie aktyviai bandė. Bet kai pažvelgėme giliau, problema pasirodė esanti dvejopa.

### Ką iš tikrųjų užduotis prašo

`write_article` fazė prašo mokinio parašyti **vieną žinutę draugams**, kurioje būtų **abu** pagrindiniai radiniai:
1. Mokytojas Petryla padarė klaidą (jo paties užrašai apie sistemą — „patikrinti pirmadienį", bet niekada nepatikrino)
2. „EduVault" privatumo politika saugo mokinių duomenis 10 metų

Ši vieninga žinutė nėra atsitiktinė — ji bus „paskelbta" ir parodyta 2-ojoje užduotyje (komentarų skiltyje), tarsi mokinys ją būtų patalpinęs grupės pokalbyje. Tai pedagogiškai svarbu: studentas pamato, kaip jo paties žodžiai grįžta į kontekstą.

### Tų 20 užstrigusių mokinių anatomija

| Kas atsitiko | Mokinių |
|---|---|
| Gavo Makarono raginimą rašyti, bet visiškai nespėjo atsakyti — laiko trūkumas | 6 |
| Atsakė vieną kartą, Makaronas paprašė daugiau, neatsakė | 5 |
| Atsakė 2-3 kartus, Makaronas vis ragino | 3 |
| Atsakė 4+ kartus — užstrigo cikle | 2 |
| Niekada nepasiekė rašymo raginimo (užfiksuoti `discuss` užbaigime) | 4 |

Iš esmės: **maždaug pusė tiesiog pritrūko laiko**. Kita pusė — **bandė rašyti, bet užstrigo cikle**, kurį sukūrė pats Makarono prompt'as.

### Ką rodo tikri dialogai

Štai mokinys (sesija `13426738`), kuris **padengė abu punktus** per atskiras žinutes, bet niekada nebaigė užduoties:

```
Mokinys: "Jie turi zinoti, kad ne tik i straipsnio patekta informacija reikia
         remtis... pacio asmens papasakota istorija is kurios kai kuriuos
         faktus isima... ir pats mokytojas nebuvo baiges konfiguracijos"
                                                    ↑ PETRYLOS KLAIDA PAMINĖTA

Makaronas: "Gera pradžia, Petrylos klaidą jau paminėjote. Bet nepamirškite
           antrosios medalio pusės..."

Mokinys: "Jus galita naudoti sia programa, bet perskaitykite atidziai...
         ar jums reikia jog duomenis saugotu 10 metu"
                                       ↑ PRIVATUMO PROBLEMA PAMINĖTA

Makaronas: "Beveik pavyko! Bet... žinutėje turi būti aiškiai paminėti abu
           dalykai KARTU"

Mokinys: "Petryla perspejo apie sauguma, bet jo nepaklause o pats eduvault
         nera saugi programa"

Makaronas: "Jūs paminėjote perspėjimą, bet pamiršote jo paties užrašus..."

[...dar bandymai, bet sesija baigiasi nepabaigta...]
```

**Mokinys padengė abu punktus.** Tik per skirtingas žinutes. Makaronas reikalavo „sujungti į vieną" ir niekada nepriėmė atskirų atsakymų kaip pakankamų. Tai nėra mokytojiškumo klausimas — tai realus UX šuolis.

### Skausmingiausias atvejis (sesija `30abd776`)

Šis mokinys padengė viską detaliai per visą dialogą, parašė ilgus apgalvotus atsakymus. Po to, kai Makaronas vis prašė „sujungti", mokinys parašė:

> **„Tai jau parašiau ir sakiau"**
> *(Makaronas vėl klausia)*
> **„As jau parašiau zinute pakartok ka as parašiau arba padaryk tu"**

Mokinys buvo teisus. Jis tikrai jau buvo viską parašęs. Bet Makarono reikalavimas „vienos sujungtos žinutės" pavertė sėkmingą mokymosi pokalbį į varginantį ciklą.

### Mažesnis, bet juokingas atvejis (sesija `2927331f`)

Po puikiai atlikto tyrimo, šis mokinys pradėjo `write_article` fazę savo žinutę draugams būtent tokia pradžia, kokios mes ir prašome („žinutė į grupės pokalbį"):

> **„hey, ar matete naujineas"**

Tai literally yra natūraliausias įmanomas pradėjimas — paauglio žinutė į grupės pokalbį. Bet Makaronas atsakė:

> *„Gera pradžia, bet draugai juk iškart paklaus: 'Kokių naujienų?'..."*

Užuot priėmęs tai kaip natūralų žinutės pradžią ir leidęs studentui tęsti, Makaronas paragino iš karto pateikti viską. Studentas neatsakė.

### Vinga'os hipotezė buvo teisinga, bet ne visai

Vinga galvojo, kad mokiniai neperpranta abiejų pusių. **Realiai jie perprato** — net 10 iš 20 užstrigusių mokinių aktyviai paminėjo abu punktus dialogo metu. Bet Makaronas jų neatpažino kaip „visos žinutės", nes ieškojo vieno sujungto sakinio.

### Kodėl tai svarbu

Jei pataisytume šią vieną problemą — **bent 10 papildomų mokinių (11% visos klasės)** būtų sėkmingai pabaigę 1 užduotį. Plius 6 mokiniai, kurie pritrūko laiko, gautų kelias papildomas minutes, jei būtų sutrumpintos ankstesnės fazės. Iš viso ~16-20 papildomų sesijų galėtų pasiekti pabaigą — tai didžiulis šuolis nuo vieno tikslinio pataisymo.

### Apribojimas, kurio negalime pamiršti

Mes negalime tiesiog leisti, kad mokiniai siųstų bet kiek atskirų žinučių. Užduoties dizainas reikalauja **vienos** vieningos žinutės, nes ji bus „paskelbta" ir rodoma 2-ojoje užduotyje kaip mokinio žinutė klasės draugams. Be vienos žinutės, antroji užduotis nebeveikia.

**Sprendimas: AI sintezė.** Kai dialogo metu mokinys padengia abu punktus (per vieną ar per kelias žinutes), Makaronas turi pats sujungti tai į vieną žinutę ir parodyti studentui:

> *„Gerai — jūsų žinutė draugams: 'Petryla pamiršo patikrinti sistemos užrašus, o EduVault saugo mūsų duomenis 10 metų. Tikrinkit, ką diegiat.' Tai paskelbsime jūsų klasės draugams. Eikime toliau."*

Studentas pamato, kas bus paskelbta. Jam nereikia patikrinti, ar viskas „sujungta teisingai". Jam nereikia kovoti su Makaronu dėl formuluotės. AI padaro sintezę pats, nes AI yra geras šitame.

---

## 5. Pirmojo "stalo" mokiniai (5 atvejai)

5 mokiniai užstrigo **`discuss` fazėje** ir niekada nepasiekė `write_article`. Šie mokiniai aktyviai dalyvavo (mediana 10 dialogo posūkių, vidutinė žinutės ilgis 52 simboliai) — jiems tiesiog **pritrūko laiko**, kol Makaronas sutiko, kad jie supranta.

Tai antras Makarono elgesio signalas: net `discuss` fazė kartais reikalauja daugiau posūkių nei turime laiko.

---

## 6. Anomalijos — ko NĖRA duomenyse

Šie dalykai NEpasitaikė, kas yra geras ženklas:

- **Jokios `Hmm... pabandykite dar kartą` klaidos pranešimų** — Gemini API veikė be pertrūkių
- **Jokių `on_max_exchanges` baigčių** — vertintojas niekada nepriverstinai nutraukė pokalbio
- **Jokių pasikartojančių žinučių** — ne botai, ne kopijavimas-įklijavimas
- **Visos `discuss` fazės baigėsi `on_success`** — vertintojas dirba savo darbą
- **Tinklo užduotyje (3-ioji) nėra `exchange` įrašų** — tai tikėtasi (statinė užduotis)

Techniniai dalykai veikia. Problema — pedagoginis tempas ir Makarono elgesys konkrečioje fazėje.

---

## 7. Rekomendacijos — kas keisti pirmiausia

### Prioritetas 1: AI sintezė `write_article` fazėje (didžiausias ROI)

Makarono prompt'as `write_article` fazei turi nustoti reikalauti, kad mokinys pats „sujungtų" abu radinius į vieną žinutę. Vietoj to, kai dialogo metu (per `discuss` ir `write_article`) mokinys padengia abu punktus — net jei per kelias atskiras žinutes — **Makaronas turi pats juos sujungti į vieną tekstą ir parodyti studentui** kaip „štai tavo žinutė draugams, ją paskelbsime".

Konkrečiai:
- **AI sintezė vietoj reikalavimo „sujungti".** Makaronas seka, ar abu radiniai paminėti dialoge. Kai jie paminėti, jis sukomponuoja vieną sklandų sakinį-žinutę ir parodo studentui patvirtinimui.
- **Studentas mato, kas bus „paskelbta".** Tai išsprendžia du dalykus iš karto: pašalina varginantį „sujunk pats" ciklą ir suteikia studentui pasitenkinimo jausmą („mano žodžiai virto kažkuo realiu").
- **Vertintojo `write_article` checklist'as turi būti trumpas.** Jis tikrina tik tiek: ar AI sintezė įvyko, ar studentas ją priėmė.
- Sukurta sintezė tampa artefaktu, kuris išsaugomas į `session.generated_artifacts` ir parodomas 2-ojoje užduotyje (kaip dabar).

**Failai, kuriuos reikia keisti:**
- `prompts/tasks/task-petryla-001/trickster_base.md` — perrašyti `write_article` skyrių, instruktuoti AI sintezę vietoj reikalavimo sujungti
- `backend/ai/trickster.py` — užtikrinti, kad student_article artefakto saugojimo kelias gali priimti AI sugeneruotą sintezę (ne tik paskutinę studento žinutę)
- `content/tasks/task-petryla-001/task.json` — `evaluator_checklist` `write_article` fazei pakoreguoti

**Tikėtinas poveikis:** ~10 papildomų mokinių (cikle užstrigusieji) baigia užduotį iš karto. Plius 6 mokiniai, kurie pritrūko laiko, gauna kelias minutes atgal, jei sutrumpinsime ir ankstesnes fazes (žr. Prioritetas 2). Iš viso ~16-20 papildomų baigtų sesijų — +18-22% baigimo rodiklis nuo vieno tikslinio promtų pataisymo.

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

2. **AI veikia.** Makaronas ir vertintojas neturi techninių klaidų. Kiekviena dialogo sesija pasiekė `on_success`. Promptai veikia. Bet `write_article` fazės prompt'as yra per griežtas — mokiniai jį padengia, bet ne taip, kaip Makaronas tikisi.

3. **Tempo nesutampa.** Turinys yra ~50 minučių vertės. Pamoka yra 30 minučių. Reikia arba sutrumpinti turinį, arba ilgesnių pamokų. Pirmas variantas yra realistiškesnis.

Taip pat: **`write_article` šuolis nuo skardžio** yra svarbiausia konkreti problema, kurią galime ištaisyti vienu pataisymu — ir tai duotų didžiausią efektą.

---

*Ataskaita parengta iš telemetrijos duomenų, surinktų po 2026-04-07 testavimo. Visi skaičiai ir citatos yra iš tikrų mokinių sesijų.*

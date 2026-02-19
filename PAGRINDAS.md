# Makaronas Pagrindas
*Inžineriniai principai edukacinei DI platformai*

## Paskirtis

Šis dokumentas nustato Makaronas platformos projektavimo ir inžinerinius principus. Tai objektyvas, per kurį peržiūrimas kiekvienas vizijos dokumentas, fazės planas ir implementacijos sprendimas.

Makaronas nėra eilinė interneto aplikacija. Tai edukacinis įrankis, naudojantis dirbtinį intelektą mokyti paauglius atpažinti žiniasklaidos manipuliacijas. Mokiniai yra nepilnamečiai. DI yra priešiškas pagal dizainą. Turinys liečia jautrias temas. Kiekvienas principas čia egzistuoja tam, kad užtikrintume, jog kuriame kažką **saugaus, efektyvaus, sąžiningo ir prižiūrimo** — būtent tokia tvarka.

---

## Apimtis

### Ką kuriame
Interaktyvią platformą, kurioje DI valdomas priešiškas dialogas moko mokinius atpažinti žiniasklaidos manipuliacijas — antraštes, selektyviai parinktas citatas, sufabrikuotas citatas, struktūrinį šališkumą, socialinę inžineriją ir psichologinius trigerius, kurie visa tai įgalina.

### Kam skirta
- **Mokiniams:** 15–18 metų amžiaus (pradinė apimtis). Ateityje gali būti išplėsta jaunesnėms ir vyresnėms amžiaus grupėms. Visi projektavimo sprendimai orientuojasi į jauniausią amžiaus ribą.
- **Mokytojams:** Planuoti mokymo programą, pasirinkti užduočių sekas, peržiūrėti anoniminę klasės lygio statistiką.
- **Turinio autoriams:** Kurti naujas užduotis naudojant šablonus ir kasetės formatą.

### Mastas
- **Bandomasis:** 5 mokyklos (~150–300 mokinių)
- **Pirmas etapas:** 100 mokyklų (~3 000–6 000 mokinių)
- **Pilnas tikslas:** 800 mokyklų (~24 000–48 000 mokinių)

### Ko NEKURIAME
- Faktų tikrinimo įrankio
- Socialinių tinklų stebėjimo sistemos
- Mokinių sekimo platformos
- Vertinimo sistemos

---

## Principai

### 1. Treniruok pauzę (Misija)
*Šūkis: „Pergalė — tai dvejojimas prieš paspaudžiant „Dalintis"."*

Kiekviena funkcija, kiekviena užduotis, kiekviena DI sąveika tarnauja vienam tikslui: mokyti mokinius sustoti prieš reaguojant. Ne viską nepasitikėti — galvoti prieš veikiant.
- **Patirtis, ne paskaita.** Mokiniai mokosi būdami apgauti, o ne klausydami, kaip apgaulės atrodo.
- **Instinktas, ne žinios.** Tikslas — ištreniruotas refleksas, ne įsiminta manipuliacijos technikų sąrašas.
- **Augimas, ne balai.** Jokių taškų, pažymių, lyderių lentelių. Platforma seka modelius ir augimą, ne pasiekimus.

### 2. Moralinis pranašumas (Nekeičiama)
*Šūkis: „Jei platforma manipuliuoja mokiniu — jau pralaimėjome."*

Trickster yra priešiškas. Platforma — ne. Šis skirtumas yra šventas.
- **Jokių tamsių šablonų.** Jokio slinkties greičio sekimo, jokių melagingų teiginių apie emocinę būseną, jokio sekimo, pridengto pedagogika.
- **Sąžiningi atskleidimai.** Po kiekvieno triuko Trickster pasakoja mokiniui tiksliai, ką padarė ir kaip. Jokios paslėptos manipuliacijos, kuri nebūtų paaiškinta.
- **Pagarba mokiniui.** Paaugliai yra aštrūs. Jie žino, kai su jais elgiamasi iš aukšto, kai juos seka ar manipuliuoja iš tikrųjų. Platforma pelno pasitikėjimą būdama skaidri apie savo metodus.
- **Turinio ribos.** Jokios tikros žalingos dezinformacijos (sveikata, smurtas, savižala). Manipuliacijos yra teatrališkos ir aiškiai edukacinės. Temos yra aktualios, bet ne traumuojančios.

### 3. Mokinių duomenys kaip šventa pareiga (GDPR ir daugiau)
*Šūkis: „Esame nepilnamečių duomenų saugotojai. Elkitės atitinkamai."*

Tai nėra pasirenkama. Tai nėra varnelė. Tai pamatas.
- **Duomenų minimizavimas.** Saugoti tik tai, kas reikalinga adaptyviam mokymui. Jokio neapdoroto pokalbio teksto saugojimo ilgiau nei 24 valandų sesiją.
- **Pseudonimizavimas.** Mokiniai yra nepermatomi ID. Platforma niekada nemato vardų, el. paštų ar jokios asmeninės informacijos. Autentifikacijos sistema susieja tapatybes — platforma to nedaro.
- **Teisė į ištrynimą.** Vienas API kvietimas ištrina viską. Struktūriškai užtikrinta, ne politika paremta.
- **Teisė į prieigą.** Mokiniai (ar jų globėjai) gali eksportuoti visus saugomus duomenis suprantamu formatu.
- **Tikslo apribojimas.** Mokymosi profilio duomenys skirti tik adaptyviam mokymui. Niekada vertinimui, elgesio įvertinimui, drausminėms priemonėms ar dalinimui už mokytojo anoniminės klasės peržiūros ribų.
- **Jokios asmeninės informacijos žurnaluose.** Užklausų žurnalai naudoja nepermatomus ID. DI kvietimų žurnalai seka žetonus ir vėlinimą, ne turinį.
- **Sutikimas prie vartų.** Platforma preziumuoja sutikimą, kai egzistuoja galiojanti sesija. Sutikimo gavimas yra autentifikacijos sluoksnio atsakomybė — platformos atsakomybė yra jo nusipelnyti.
- **Projektuota auditui.** Kiekvienas duomenų srautas turi būti paaiškinamas reguliuotojui. Jei negalite nupiešti diagramos, kur keliauja mokinio duomenys ir kas juos mato — architektūra yra neteisinga.

### 4. Nesenstantis turinys (Galiojimo laiko taisyklė)
*Šūkis: „Jei pasens per metus — jam čia ne vieta."*

Dezinformacijos taktikos yra amžinos. Jas iliustruojantys scenarijai taip pat turėtų būti.
- **Jokių aktualijų.** Jokių populiarių temų, jokių tikrų viešų asmenų, jokių nuorodų į konkrečius pastaruosius įvykius.
- **Jokio platformų ženklinimo.** Scenarijai evokuoja „socialinių tinklų srautą" ar „grupės pokalbį", ne „TikTok" ar „WhatsApp" vardu. Platformos ateina ir nueina; manipuliacijos gramatika lieka.
- **Fiktyvu, bet realistiška.** Scenarijai turi atrodyti tikėtini, bet nebūti susiejami su tikrais įvykiais.
- **Psichologiniai trigeriai yra konstanta.** Skubumas, priklausymas, neteisybė, godumas, cinizmas — jie nesikeičia. Kurkite aplink juos.

### 5. Evokuok, neimituok (Sąsajos taisyklė)
*Šūkis: „Teatro dekoracijos, ne kino aikštelės."*

Platforma pristato užduotis terpėse, kurias paaugliai atpažįsta — bet niekada neapsimeta tomis terpėmis.
- **Jokios netikros telefono sąsajos.** Jokių tobulų TikTok kopijų, jokių imituotų pranešimų juostų. Paaugliai akimirksniu atpažįsta suaugusiųjų kostiuminį šou ir nusisuka.
- **Evokuojantis dizainas.** Pokalbio užduotis jaučiasi kaip pokalbis — žinučių burbulai, laiko žymos, slapyvardžiai. Bet tai aiškiai platforma, ne „WhatsApp" ekrano nuotrauka.
- **Sąžiningas įrėminimas.** Platforma yra treniruočių aplinka. Ji taip ir sako. Trickster yra melagis, ne platforma.

### 6. Pagrindinis DI principas (Kodėl DI čia svarbus)
*Šūkis: „DI užsitarnauja savo kainą reaguodamas į tai, ką šis konkretus mokinys iš tikrųjų pasakė ir padarė."*

DI nėra naudojamas dėl naujumo. Jis naudojamas ten, kur yra nepakeičiamas — kur statinis turinys negali atlikti darbo.
- **Priešiškas pokalbis.** DI atremia mokinio skepticizmą: „Ką konkrečiai? Šaltinis tikras." Statinis išsišakojimas to negali.
- **Valdomas atradimas.** DI susiaurina paiešką, kai mokinys stringa, nukreipdamas link to, ko ieškoti, neduodamas atsakymo.
- **Veidrodis per užduotis.** DI laiko mokinio istoriją ir konfrontuoja su jo paties modeliais per sesijas.
- **Adaptyvus taikymas.** DI pakeičia atakos vektorių pagal kiekvieno mokinio konkrečią silpnybę.
- **Empatijos apvertimas.** DI vertina, kai mokiniai bando patys kurti manipuliacijas.
- **Kalibruotas vertinimas.** Kai kuriose užduotyse manipuliacijos nėra. DI aptinka, kai mokiniai klaidingai apkaltina teisėtą turinį.
- **Lakmuso popierėlis.** Kiekvienai DI valdomai funkcijai klauskite: „Ar statinis išsišakojimo kelias veiktų taip pat gerai?" Jei taip — darykite statinį. DI rezervuotas ten, kur jis nepakeičiamas.

### 7. Dvigubas raštingumas (Platforma kaip mokytojas)
*Šūkis: „Platforma PATI yra DI raštingumo pamoka."*

Platforma moko ir informacinio, ir DI raštingumo — ne kaip atskirus modulius, bet per savo pačios egzistavimą.
- **Mokiniai patiria DI manipuliaciją tiesiogiai.** Trickster yra DI. Jis jiems tai pasako. Pamoka: mašina ką tik tai jums padarė, ir ji gali tai padaryti milijonams vienu metu.
- **Mokytojai patiria DI bendradarbiavimą.** Composer rodo savo samprotavimus, priima korekcijas, paaiškina savo pasirinkimus. Jis modeliuoja, kaip atrodo sveika žmogaus ir DI sąveika.
- **Ketvirtosios sienos laužymas.** Svarbiausiais momentais Trickster visiškai iškrenta iš vaidmens ir kalba kaip DI apie tai, ką DI gali. Tai giliausias mokymo momentas.

### 8. Komandos prieinamumas (Perdavimo taisyklė)
*Šūkis: „Jei komanda negali to pakeisti be originalaus autoriaus — tai nebaigta."*

Platformą prižiūrės techninė komanda be dedikuoto DI specialisto. Viskas turi būti prieinama.
- **Instrukcijos yra paprastas Markdown.** Jokios specialios sintaksės, jokio kodo. Komanda atidaro failą, perskaito, pakoreguoja. Git seka pakeitimus.
- **Modelio keitimas — viena eilutė.** Pakeiskite modelio ID `models.py` faile, pasirinktinai parašykite modeliui specifinį instrukcijos failą. Padaryta.
- **Architektūra dokumentuota su argumentacija.** Ne tik „kas", bet ir „kodėl". Būsimi prižiūrėtojai turi suprasti sprendimų logiką, ne tik sekti instrukcijas.
- **Kabliai aiškiai pažymėti.** Kiekvienas stub sako, ką jis daro, kas jį pakeičia ir kokią sąsają reikia patenkinti.
- **DI sudėtingumas inkapsuliuotas.** Konteksto valdymo sluoksnis (sluoksniavimas, biudžetavimas, prioritetizavimas) yra sudėtingas, bet dokumentuotas pakankamai, kad kompetentingas programuotojas galėtų derinti ir modifikuoti.

### 9. Kaštų sąmoningumas (Žetonų mokestis)
*Šūkis: „Kiekvienas DI kvietimas turi kainą. Kiekvienai kainai reikia pagrindimo."*

Su 800 mokyklų nerūpestingas žetonų naudojimas virsta biudžeto krize.
- **Modelių pakopavimas.** Naudokite pigiausią modelį, atitinkantį kokybės reikalavimus. Flash Lite paprastiems vertinimams, galingesni modeliai sudėtingam dialogui.
- **Modelio parinkimas pagal užduotį.** Ne kiekvienai užduočiai reikia pajėgiausio modelio. Kasetės formatas nurodo, kuriai modelių šeimai užduotis teikia pirmenybę.
- **Statinė, kur įmanoma.** Statinės užduotys kainuoja nulį vienam mokiniui. DI/statinis užduočių santykis yra sąmoningas kaštų svertas, ne antraeilis dalykas.
- **Žetonų biudžetai.** Konteksto valdiklis užtikrina biudžetus kiekvienam DI kvietimui. Jei kontekstas viršija biudžetą, jis apkarpo protingai, o ne sugenda.
- **Naudojimo žurnalavimas.** Kiekvienas DI kvietimas fiksuoja: naudotą modelį, žetonus vidun, žetonus lauk, vėlinimą. Kaštų matomumas nuo pirmos dienos.

### 10. Grakštus degradavimas (Atsarginė)
*Šūkis: „DI yra priedas, ne priklausomybė."*

DI suges. Modeliai krenta. Limitai pasiekiami. Mokinys niekada neturi matyti tuščio ekrano.
- **Statinė atsarginė.** Jei Trickster negali atsakyti, užduotis grįžta prie statinių išsišakojimo kelių (jei jie egzistuoja) su pastaba, kad DI laikinai neprieinamas.
- **Laiko biudžetai.** DI kvietimams taikomi griežti laiko limitai. Mokinys, laukiantis ilgiau nei 5 sekundes pokalbio užduotyje, jau prarado dėmesį. Geriau rodyti grakščią atsarginę nei suktuką.
- **Klaida kaip orientyras.** Jei DI sugenda, klaidos pranešimas pasako mokiniui (ar mokytojui), kas nutiko ir ką daryti: „DI per daug galvoja. Bandykite dar kartą arba pereikite prie kitos užduoties."

### 11. Struktūrinė izoliacija (Pertvarų taisyklė)
*Šūkis: „Sugedusi instrukcija niekada neturi numušti platformos."*

Architektūra apsaugo nuo kaskadų.
- **DI sluoksnis izoliuotas.** Bloga instrukcija, modelio laukimo limito viršijimas ar tiekėjo gedimas paveikia tik DI atsakymus — ne maršrutizavimą, ne būsenos valdymą, ne mokytojo skydelį.
- **Kabliai yra ribos.** Autentifikacija, duomenų bazė, saugykla yra keičiami, nes yra už sąsajų. Duomenų bazės migracija neliečia DI kodo. Autentifikacijos pakeitimas neliečia užduočių logikos.
- **Frontend nepriklausomas.** Frontend naudoja API. Jis gali būti perkurtas, perdažytas ar pakeistas neliečiant backend.
- **Užduotys savarankiškos.** Sugedusi užduočių kasetė paveikia tik tą užduotį. Kitos užduotys veikia toliau.

### 12. DI išvesties saugumas (Apsauginis turėklas)
*Šūkis: „Trickster yra priešiškas pagal dizainą. Apsaugos nėra pasirenkamos."*

Instrukcijos modeliui yra pasiūlymai, ne garantijos. Platformoje, kur priešiškas DI kalba su nepilnamečiais, saugumas turi būti užtikrinamas programiškai — ne tikintis geriausio.
- **Išvesties validacija.** DI atsakymai praeina turinio saugumo patikrą prieš pasiekdami mokinį. Atsakymai, peržengiantys turinio ribas (tikra žala, tikra neapykanta, tikri asmeniniai puolimai), sugaunami ir pakeičiami saugia atsargine — ne tyliai, bet su užfiksuotu incidentu.
- **Temų ribos yra kodas, ne proza.** Draudžiamų turinio sričių sąrašas (savižala, tikras smurtas, seksualinis turinys, tikra radikalizacija) apibrėžtas struktūrizuotu formatu, kurį saugumo sluoksnis gali tikrinti — ne palaidotas instrukcijoje, kurią modelis gali ignoruoti.
- **Eskalacija ribota.** Trickster adaptuojasi ir stumia atgal — bet yra lubos. Sistema seka pokalbio intensyvumą ir įsikiša, jei priešiškas spaudimas peržengia ribą, nepriklausomai nuo to, ką sako instrukcija.
- **Instrukcijų pakeitimų regresija.** Bet koks Trickster instrukcijų pakeitimas testuojamas prieš saugumo testų rinkinį prieš diegimą. Instrukcijos pakeitimas, praeinantis kokybės testą, bet nepraeinantis saugumo testo — nediegiamas.
- **Modelio pakeitimo validacija.** Keisti modelius (8 principas) lengva. Bet naujas modelis gali elgtis kitaip esant priešiškam spaudimui. Modelio pakeitimai reikalauja saugumo vertinimo, ne tik funkcinio.

### 13. Saugumas pagal dizainą (Užrakinta klasė)
*Šūkis: „Mokome mokinius galvoti kaip atakuotojai. Tarkime, kad taip ir darys."*

Ši platforma tvarko nepilnamečių duomenis, mokytojų programas ir DI sistemas, su kuriomis mokiniai sąveikauja tiesiogiai. Saugumas nėra funkcija — tai apribojimas kiekvienam projektavimo sprendimui.
- **Apsauga nuo instrukcijų injekcijos.** Mokiniai rašo laisvos formos tekstą, kuris pasiekia DI. Jie bandys nulaužti Trickster. Įvesties valymas, išvesties validacija ir sisteminių instrukcijų izoliacija yra privalomi — ne todėl, kad mokiniai yra piktavališki, o todėl, kad mes juos išmokėme tirti.
- **Nuomininko izoliacija.** Mokyklos A mokinys niekada neturi matyti mokyklos B duomenų. Mokytojas niekada neturi matyti kitos mokyklos programų. Daugelio nuomininkų ribos užtikrinamos duomenų sluoksnyje, ne tik sąsajoje.
- **Mažiausia privilegija.** Mokiniai mato savo duomenis. Mokytojai mato anoniminę klasės lygio statistiką. Administratoriai mato mokyklos lygio suvestines. Jokia rolė nemato daugiau nei reikia. API galutiniai taškai tai užtikrina, ne tik frontend.
- **Jokių paslapčių kliente.** API raktai, modelių kredencialai ir vidiniai galutiniai taškai niekada nepasiekia naršyklės. Frontend yra nepatikimas.
- **Greičio ribojimas.** DI galutiniams taškams taikomi limitai pagal mokinį ir pagal mokyklą. Vieno mokinio nevaldoma sesija neturi išsekinti mokyklos žetonų biudžeto ar platformos API kvotos.
- **Audito pėdsakas.** Autentifikacijos įvykiai, rolių pakeitimai, duomenų eksportai ir duomenų trynimai fiksuojami. Ne sekimui — atskaitomybei, kai kažkas nueina ne taip.
- **Klaidų užtemimas.** Vidinės klaidos grąžina bendrinius pranešimus mokiniams. Stack trace, modelių pavadinimai ir sistemos keliai niekada nepatenka į klientą. Derinimo informacija gyvena serverio žurnaluose, ne HTTP atsakymuose.
- **Duomenų bazės disciplina.** Kiekviena užklausa naudoja parametrizuotus teiginius — jokio eilučių interpoliavimo, jokių išimčių. Visa duomenų bazės prieiga eina per duomenų sluoksnio sąsają, niekada tiesiogiai iš maršrutų tvarkyklių. Schemos migracijos peržiūrimos dėl duomenų atskleidimo. Atsarginės kopijos ir atkūrimo procedūros egzistuoja ir yra ištestuotos. Prisijungimo kredencialai — aplinkos kintamieji, niekada neįkelti į versijavimo sistemą.
- **Priklausomybių higiena.** Trečiųjų šalių paketai fiksuojami ir peržiūrimi. Edukacinės platformos, skirtos nepilnamečiams, atakos paviršius nėra vieta avangardiniams paketams.

### 14. Prieinamumas ir įtrauktis (Atviros durys)
*Šūkis: „Edukacinė infrastruktūra yra visiems."*

Šią platformą naudos įvairūs mokiniai šimtuose mokyklų.
- **Navigacija klaviatūra.** Kiekviena sąveika pasiekiama be pelės.
- **Ekrano skaitytuvo palaikymas.** Turinio skydeliai, mygtukai, pokalbio žinutės — viskas tinkamai pažymėta.
- **Paruošta lokalizacijai.** Lietuvių kalba yra pagrindinė. Latvių ir anglų kalbos planuojamos. Architektūra palaiko kalbų paketus nuo pirmos dienos be perdirbimo.
- **Kognityvinė apkrova.** Aiški, rami sąsaja. Jokio vizualinio pertekliaus. Trickster teatrališkumas gyvena tekste, ne blyksiniuose sąsajos elementuose.
- **Naršyklė pirma.** Standartinė interneto aplikacija. Stalinio kompiuterio naršyklė yra pagrindinis tikslas. Prisitaikantis dizainas yra pageidautinas, ne reikalavimas. Mobilios programėlės yra ateities klausimas, ne pradinė apimtis.
- **Paruošta balso režimui.** Akli mokiniai gali bendrauti su DI balsu be ekrano skaitytuvo — platformos pokalbio šerdis yra natūraliai suderinama su balsu. Kad šis kelias liktų atviras: API atsakymai turi būti semantiniai (turinys, ne atvaizdavimo instrukcijos), užduočių kasetėse turi būti tekstiniai vizualinių išteklių aprašymai, vertinimas turi spręsti pagal tai, ką mokinys *pasakė*, o ne kaip *paspaudė*, ir laiko biudžetai turi būti konfigūruojami pagal modalumą.

### 15. Multimodalus mokymasis (Visos smegenys)
*Šūkis: „Ne visi mokosi skaitydami."*

Platforma palaiko kelis mokymosi modalumus — bet tik ten, kur jie tarnauja užduočiai.
- **Vizualinis.** Klaidinančios diagramos, iš konteksto ištraukti vaizdai, memai, DI sugeneruoti vaizdai. Vaizdai yra pirmo lygio turinio blokai, ne dekoracijos.
- **Garsinis.** Balso žinutės, balso tono manipuliacija, podcast klipai. Garso ištekliai palaikomi užduočių formate.
- **Skaitymo/rašymo.** Stuburas. Straipsniai, įrašai, laisvos formos tekstiniai atsakymai.
- **Kinestetinis (skaitmeninis).** Tyrimo medžiai, laiko juostos slinkimas, fizinis atsakymo rašymo veiksmas esant socialiniam spaudimui.
- **Iš anksto sukurti ištekliai.** Multimodalus turinys kuriamas ir peržiūrimas, o ne generuojamas realiuoju laiku. Kokybė ir kaštai kontroliuojami.

### 16. Sąžininga inžinerija (Pragmatizmo principas)
*Šūkis: „Išleisk tai, kas veikia. Dokumentuok, kas trūksta. Neapsimetinėk."*

Tai savanorių kuriama platforma su tikrais apribojimais. Kuriame sąžiningai jų ribose.
- **Stub'ai yra sąžiningi.** Netikra autentifikacijos paslauga sako „STUB — grąžina testinį vartotoją." Ji neapsimeta autentifikuojanti.
- **Apimtis deklaruota.** Kiekvienas vizijos dokumentas sako, kas yra apimtyje ir kas sąmoningai atidėta. Jokių „pasirinktinių" elementų, kurie kuria dviprasmybę.
- **Kompromisai dokumentuoti.** Kai renkamės greitį prieš lankstumą (ar atvirkščiai), užrašome kodėl. Būsimiems prižiūrėtojams reikia argumentacijos.
- **Techninė skola įvardinta.** Jei trumpiname kelią, pažymime. „Ši atminties saugykla neišliks perkrovus. Žr. hooks/database.py dėl sąsajos, kurią komanda implementuoja."

---

## Peržiūros kontrolinis sąrašas

Peržiūrint vizijos dokumentą, fazės planą ar implementaciją, naudokite šiuos klausimus:

### Saugumas ir etika
- Ar ši funkcija gerbia mokinį? Ar 15-metis jaustųsi gerbiamas, ar sekamas?
- Ar saugomi kokie nors mokinio duomenys viršijantys būtinybę? Ar jie gali būti ištrinti?
- Ar Trickster atskleidžia viską, ką padarė? Ar yra paslėpta manipuliacija, kuri nepaaiškinta?
- Ar turinys nesenstantis? Ar jis atrodys pasenęs ar netinkamas po 2 metų?

### DI pagrindimas
- Ar šiai funkcijai reikia DI? Ar statinis išsišakojimas veiktų taip pat gerai?
- Ar DI reaguoja į tai, ką šis konkretus mokinys pasakė ir padarė?
- Kas nutiks, jei DI suges? Ar yra atsarginė?
- Kokia žetonų kaina vienam mokiniui? Ar modelio pasirinkimas pagrįstas?
- Ar DI išvestis praeina saugumo patikrą prieš pasiekdama mokinį? Kas nutiks, jei modelis sugeneruoja kažką už turinio ribų?

### Komandos perdavimas
- Ar komanda gali tai modifikuoti be DI ekspertizės?
- Ar instrukcijos yra paprastame Markdown? Ar modelis keičiamas?
- Ar argumentacija dokumentuota, ne tik struktūra?
- Ar stub'ai ir kabliai aiškiai pažymėti?

### Mokinio patirtis
- Ar tai palaiko mokinio įsitraukimą? Ar yra negyva zona, kur mokinys stringa be orientyrų?
- Ar tai prieinama naršyklėje? Su ekrano skaitytuvu? Lietuviškai?
- Ar sudėtingumas adaptuojasi prie mokinio, ar yra visiems vienodas?

### Saugumas
- Ar mokinio laisvos formos įvestis gali pasiekti DI be valymo? Koks instrukcijų injekcijos paviršius?
- Ar nuomininko izoliacija užtikrinta duomenų sluoksnyje? Ar suklastota užklausa galėtų nutekinti tarp-mokyklinius duomenis?
- Ar šis galutinis taškas užtikrina rolėmis paremtą prieigą, ar pasitiki frontend?
- Ar klaidų atsakymai neatskleidžia vidinių detalių (kelių, modelių pavadinimų, stack trace)?
- Ar DI naudojantys galutiniai taškai turi greičio ribojimą?
- Ar visos duomenų bazės užklausos naudoja parametrizuotus teiginius? Ar kokia nors vartotojo įvestis pasiekia užklausą neeidama per duomenų sluoksnį?

### Mastas ir kaštai
- Kas nutiks su 800 mokyklų? Ar tai plečiasi horizontaliai?
- Kokia DI kaina vienam mokiniui? Ar yra pigesnis modelis, kuris veiktų?
- Ar yra statinė alternatyva biudžetą ribojančioms diegimams?

---

*Pagrindo versija: 1.1*
*Sukurta: 2026-02-18*
*Apimtis: Makaronas platforma (visos vizijos, visos fazės)*

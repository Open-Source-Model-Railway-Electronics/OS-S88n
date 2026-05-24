> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; 🇩🇰 DA &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-S88n Feedback-moduler Manual

**Understøtter: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Alle tre OS-S88n modulvarianter](all.png)

*Fra venstre mod højre: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introduktion

OS-S88n-modulerne leverer tilbagemeldingsfunktionalitet til DCC-modeljernbaner ved brug af den standardiserede S88n-protokol. Disse moduler muliggør realtidsovervågning af blokokkupering og anlægshændelser, og sender data til din kommandostation eller PC-baserede styresoftware.

Tre varianter er tilgængelige til at imødekomme forskellige detektionsbehov:

- **OS-S88n GND** — jordkontaktdetektion, velegnet til 3-skinne (Märklin-stil) anlæg
- **OS-S88n CS** — strømmålingsdetektion, velegnet til 2-skinne og 3-skinne digitale anlæg
- **OS-S88n OPTO** — optoisolerede digitale indgange, til brug med eksterne sensorer som IR-detektorer eller Hall-sensorer

Alle varianter inkluderer:

- Sammenkoblingsegnet S88n-stik (RJ-45)
- Skrueterminaler til alle sensorforbindelser
- Kompatibilitet med alle større kommandostationer og software (iTrain, Rocrail, Windigipet m.fl.)

---

## Modulvarianter

### OS-S88n GND — Jordkontaktdetektion

![OS-S88n GND-kort](OS-S88n-GND.png)

GND-modulet har 16 indgange, der aktiveres, når indgangen trækkes til jord. Kompatible sensorer og detektionsmetoder inkluderer:

- Reed-kontakter
- Trykknapper
- Metal-hjulsæt, der bryder begge skinner på et 3-skinne (Märklin-stil) anlæg

⚠️ **Vigtigt — 3-skinne anlæg:** Når GND-modulet bruges på et 3-skinne anlæg, **skal** din kommandostation og alle boostere være af fælles-jord-typen. Hvis din kommandostation bruger et H-bro-output, **vil brug af GND-modulet beskadige din kommandostation**. Brug OPTO-varianten i stedet i det tilfælde.

---

### OS-S88n CS — Strømmåling

![OS-S88n CS-kort](OS-S88n-CS.png)

CS-modulet har 16 indgange, der aktiveres, hver gang der trækkes strøm gennem en overvåget sporsektion. Ethvert rullende materiel, der trækker strøm, vil udløse detektion, herunder:

- Lokomotiver
- Oplyste vogne
- Godsvogne udstyret med en modstand til detektionsformål

Velegnet til både 2-skinne og 3-skinne digitale anlæg.

---

### OS-S88n OPTO — Optoisoleret indgangsdetektion

![OS-S88n OPTO-kort](OS-S88n-OPTO.png)

OPTO-modulet har 16 fuldt optoisolerede digitale indgange. Fuld galvanisk isolation mellem sensorerne og S88-bussen gør denne variant ideel til:

- IR-detektorer
- Hall-sensorer
- Kontakter placeret langt fra modulet
- Støjfølsomme miljøer
- Anlæg, hvor jordslynger eller elektrisk interferens er et problem

⚠️ OPTO-modulet detekterer **ikke** sporokkupering af sig selv — det kræver eksterne sensorer, der leverer et logik-niveau-signal.

---

## Egenskaber

- Fuldt kompatibel med S88n-tilbagemeldingsprotokollen
- RJ-45-stik til sammenkoblingsforbindelse af moduler
- 16 indgange per modul
- Stak op til 31 moduler i en enkelt kæde
- Skrueterminaler til alle sensorforbindelser
- OPTO-versionen leverer fuld galvanisk isolation

---

## Tilslutning af modulerne

### Strøm og signal

Forbind modulerne til din kommandostation ved hjælp af standard UTP Ethernet-kabler. **Alle 8 ledninger skal være forbundet** — undgå billigt fremstillede patchkabler, der udelader interne ledninger.

- **S88n OUT**-stik → kommandostationens S88n-indgang (eller det forrige moduls IN)
- **S88n IN**-stik → næste modul i kæden (lad det stå tomt på det sidste modul)

### Sensorkabeltrækning

**OS-S88n CS — strømmåling**

![Kabeltrækning af strømmålingsvarianten](image.png)

Før sporforsyningsleredningerne til hvert detektionssegment gennem strømmålings-indgangene. Ethvert tog, der trækker strøm i det segment, aktiverer den tilsvarende indgang.

---

**OS-S88n GND — jordkontakt**

![Kabeltrækning af GND-varianten](image-1.png)

Forbind én skinne (eller sensorudgang) til en indgangsterminal og den fælles skinne til COM-terminalen. Hjulsæt, der bryder begge skinner, fuldfører kredsløbet til jord og udløser indgangen.

⚠️ *Når GND-versionen bruges på et 3-skinne anlæg, er det absolut nødvendigt, at kommandostationen og boosterne er af fælles-jord-typen. Hvis du bruger GND-versionen med en H-bro-kommandostation, vil du ødelægge din kommandostation. Brug OPTO-varianten i stedet.*

---

**OS-S88n OPTO — optoisoleret**

![Kabeltrækning af OPTO-varianten](image-3.png)

Forbind din sensors signaludgang til indgangsterminalen og sensorjorden til COM-terminalen. Indgangsspændingen afhænger af din sensors forsyning; tjek kortets markeringer for det understøttede område.

---

**Sammenkoblingsforbindelse af flere moduler**

![Sammenkoblingsforbindelse af flere OS-S88n-moduler](image-2.png)

Forbind OUT fra hvert modul til IN på det næste. Det første moduls OUT går til kommandostationen. Lad IN-stikket på det sidste modul i kæden stå tomt.

---

## Fejlfinding

**Ingen tilbagemelding modtaget**
- Tjek RJ-45-kabling og bekræft, at alle 8 ledere er til stede
- Bekræft, at OUT-stikket peger mod kommandostationen (ikke IN)
- Verificer, at modulets adresseområde i din software svarer til modulets position i kæden

**Falske udløsninger**
- GND-version: tjek for kabelfejl eller interferens mellem detektionssegmenter
- CS-version: tjek minimumstrøkstrøm — vogne med kun LED-belysning kan have brug for en modstand for at udløse detektion
- OPTO-version: tjek sensorforsyningsspænding og signalpolaritet
- Undgå Ethernet-kabler længere end 5 m

**Forsinket tilbagemelding**
- Reducer afsøgningsintervallet i din kommandostation eller PC-software
- Verificer korrekt indgangsadressering i din software

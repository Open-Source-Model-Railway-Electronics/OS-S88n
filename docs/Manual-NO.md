> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; 🇳🇴 NO &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-S88n Tilbakemeldingsmoduler Manual

**Støtter: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Alle tre OS-S88n-modulvarianter](all.png)

*Fra venstre til høyre: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Innledning

OS-S88n-modulene gir tilbakemeldings-funksjonalitet for DCC-modelljernbaner ved hjelp av den standardiserte S88n-protokollen. Disse modulene muliggjør sanntidsovervåking av blokkbelegg og anleggshendelser, og sender data til sentralstasjonen din eller PC-basert styringsprogramvare.

Tre varianter er tilgjengelige for å dekke ulike deteksjonsbehov:

- **OS-S88n GND** — jordkontakt-deteksjon, egnet for 3-skinne-anlegg (Märklin-stil)
- **OS-S88n CS** — strømsansedeteksjon, egnet for 2-skinne- og 3-skinne-digitale anlegg
- **OS-S88n OPTO** — optoisolerte digitale innganger, for bruk med eksterne sensorer som IR-detektorer eller Hall-sensorer

Alle varianter inkluderer:

- Lenke-kjede S88n-koblinger (RJ-45)
- Skrueterminaler for alle sensortilkoblinger
- Kompatibilitet med alle større sentralstasjoner og programvare (iTrain, Rocrail, Windigipet, osv.)

---

## Modulvarianter

### OS-S88n GND — Jordkontakt-deteksjon

![OS-S88n GND-kort](OS-S88n-GND.png)

GND-modulen har 16 innganger som utløses når inngangen trekkes til jord. Kompatible sensorer og deteksjonsmetoder inkluderer:

- Rørbrytere
- Trykknapper
- Metallhjulsett som broer skinnene på et 3-skinne-anlegg (Märklin-stil)

⚠️ **Viktig — 3-skinne-anlegg:** Når du bruker GND-modulen på et 3-skinne-anlegg, **må** sentralstasjonen din og alle forsterkere være av fellesjord-type. Hvis sentralstasjonen din bruker H-bro-utgang, vil bruk av GND-modulen **ødelegge sentralstasjonen**. Bruk OPTO-varianten i stedet i så fall.

---

### OS-S88n CS — Strømsansing

![OS-S88n CS-kort](OS-S88n-CS.png)

CS-modulen har 16 innganger som aktiveres hver gang strøm trekkes gjennom et overvåket sporparti. Alt rullende materiell som trekker strøm vil utløse deteksjon, inkludert:

- Lokomotiver
- Belyste vogner
- Godsvogner utstyrt med motstand for deteksjonsformål

Egnet for både 2-skinne- og 3-skinne-digitale anlegg.

---

### OS-S88n OPTO — Optoisolert inngångsdeteksjon

![OS-S88n OPTO-kort](OS-S88n-OPTO.png)

OPTO-modulen har 16 fullt optoisolerte digitale innganger. Full galvanisk isolasjon mellom sensorene og S88-bussen gjør denne varianten ideell for:

- IR-detektorer
- Hall-sensorer
- Brytere plassert langt fra modulen
- Støyfølsomme miljøer
- Anlegg der jordslynger eller elektrisk interferens er et problem

⚠️ OPTO-modulen registrerer **ikke** sporsbelegg på egenhånd — den krever eksterne sensorer som gir et logikknivå-signal.

---

## Egenskaper

- Fullt kompatibel med S88n tilbakemeldingsprotokollen
- RJ-45-koblinger for kjeding av moduler
- 16 innganger per modul
- Stabble opptil 31 moduler i en enkelt kjede
- Skrueterminaler for alle sensortilkoblinger
- OPTO-versjonen gir full galvanisk isolasjon

---

## Tilkobling av modulene

### Strøm og signal

Koble modulene til sentralstasjonen din med standard UTP Ethernet-kabler. **Alle 8 ledere må være tilkoblet** — unngå billig produserte patch-kabler som mangler interne ledere.

- **S88n OUT**-kobling → sentralstasjonens S88n-inngang (eller forrige moduls IN)
- **S88n IN**-kobling → neste modul i kjeden (la stå tom på den siste modulen)

### Sensor-kabling

**OS-S88n CS — strømsansing**

![Kabling av strømsanseversjon](image.png)

Led spormatingsledn. for hvert deteksjonsparti gjennom strømsansingangene. Ethvert tog som trekker strøm i det partiet aktiverer tilsvarende inngang.

---

**OS-S88n GND — jordkontakt**

![Kabling av GND-versjonen](image-1.png)

Koble én skinne (eller sensorutgang) til en inngangsterminal og den felles skinnen til COM-terminalen. Hjulsett som broer begge skinner fullfører kretsen til jord og utløser inngangen.

⚠️ *Ved bruk av GND-versjonen på et 3-skinne-anlegg er det avgjørende at sentralstasjonen og forsterkerne er av fellesjord-type. Hvis du bruker GND-versjonen med en H-bro-sentralstasjon, vil du ødelegge sentralstasjonen. Bruk OPTO-varianten i stedet.*

---

**OS-S88n OPTO — optoisolert**

![Kabling av OPTO-versjonen](image-3.png)

Koble sensorens signalutgang til inngangsterminalen og sensorgrunnen til COM-terminalen. Inngangsspenningen avhenger av sensorens forsyning; sjekk kortets merkinger for støttet område.

---

**Kjeding av flere moduler**

![Kjeding av flere OS-S88n-moduler](image-2.png)

Koble OUT fra hver modul til IN på den neste. Den første modulens OUT går til sentralstasjonen. La IN-koblingen på den siste modulen i kjeden stå tom.

---

## Feilsøking

**Ingen tilbakemelding mottatt**
- Sjekk RJ-45-kabling og bekreft at alle 8 ledere er til stede
- Bekreft at OUT-koblingen peker mot sentralstasjonen (ikke IN)
- Verifiser at moduladresseområdet i programvaren din samsvarer med modulens posisjon i kjeden

**Falske utløsere**
- GND-versjon: sjekk for kabelkortslutninger eller interferens mellom deteksjonspartier
- CS-versjon: sjekk minimalt strømtrekk — vogner med kun LED-er kan trenge en motstand for å utløse deteksjon
- OPTO-versjon: sjekk sensorforsyningsspenning og signalpolaritet
- Unngå Ethernet-kabler lengre enn 5 m

**Forsinket tilbakemelding**
- Reduser pollingsintervallet i sentralstasjonen eller PC-programvaren din
- Verifiser korrekt inngangadressering i programvaren din

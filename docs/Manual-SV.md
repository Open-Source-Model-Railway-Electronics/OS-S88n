> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; 🇸🇪 SV &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-S88n Återkopplingsmoduler Manual

**Stöder: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Alla tre OS-S88n-modulvarianterna](all.png)

*Från vänster till höger: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introduktion

OS-S88n-modulerna tillhandahåller återkopplingsfunktionalitet för DCC-modelljärnvägar med det standardiserade S88n-protokollet. Dessa moduler möjliggör realtidsövervakning av blockövervakning och banor, och skickar data till din kommandostation eller PC-baserade styrsoftware.

Tre varianter finns tillgängliga för att passa olika detektionsbehov:

- **OS-S88n GND** — jordkontaktdetektering, lämplig för 3-skena-banor (Märklin-stil)
- **OS-S88n CS** — strömavkänningsdetektering, lämplig för 2-skena- och 3-skena-digitala banor
- **OS-S88n OPTO** — optoelektriskt isolerade digitala ingångar, för användning med externa sensorer såsom IR-detektorer eller Hall-sensorer

Alla varianter inkluderar:

- Sammankopplingsbara S88n-kontakter (RJ-45)
- Skruvplintrar för alla sensoranslutningar
- Kompatibilitet med alla större kommandostationer och program (iTrain, Rocrail, Windigipet m.fl.)

---

## Modulvarianter

### OS-S88n GND — Jordkontaktdetektering

![OS-S88n GND-kort](OS-S88n-GND.png)

GND-modulen har 16 ingångar som utlöses när ingången dras till jord. Kompatibla sensorer och detektionsmetoder inkluderar:

- Reedbrytare
- Tryckknappar
- Metallhjulsatser som bryggar räls i ett 3-skena-system (Märklin-stil)

⚠️ **Viktigt — 3-skena-banor:** När du använder GND-modulen på en 3-skena-bana **måste** din kommandostation och alla boostrar vara av gemensam jord-typ. Om din kommandostation använder en H-bryggeutgång kommer användningen av GND-modulen **att skada din kommandostation**. Använd OPTO-varianten i det fallet.

---

### OS-S88n CS — Strömavkänning

![OS-S88n CS-kort](OS-S88n-CS.png)

CS-modulen har 16 ingångar som aktiveras när ström dras genom ett övervakat spåravsnitt. All rullande materiel som drar ström utlöser detektering, inklusive:

- Lok
- Belysta vagnar
- Vagnar utrustade med ett motstånd för detektionsändamål

Lämplig för både 2-skena- och 3-skena-digitala banor.

---

### OS-S88n OPTO — Optoelektriskt isolerad ingångsdetektering

![OS-S88n OPTO-kort](OS-S88n-OPTO.png)

OPTO-modulen har 16 fullständigt optoelektriskt isolerade digitala ingångar. Fullständig galvanisk isolering mellan sensorerna och S88-bussen gör denna variant idealisk för:

- IR-detektorer
- Hall-sensorer
- Brytare placerade långt från modulen
- Brusskänsliga miljöer
- Banor där jordloopar eller elektrisk störning är ett problem

⚠️ OPTO-modulen detekterar **inte** spårbeläggning av sig självt — den kräver externa sensorer som ger en logikspänningssignal.

---

## Funktioner

- Fullt kompatibel med S88n återkopplingsprotokoll
- RJ-45-kontakter för seriekoppling av moduler
- 16 ingångar per modul
- Koppla upp till 31 moduler i en enda kedja
- Skruvplintrar för alla sensoranslutningar
- OPTO-versionen ger fullständig galvanisk isolering

---

## Anslutning av modulerna

### Ström och signal

Anslut modulerna till din kommandostation med standard UTP Ethernet-kablar. **Alla 8 ledare måste vara anslutna** — undvik billigt tillverkade patchkablar som utelämnar interna ledare.

- **S88n OUT**-kontakt → kommandostationens S88n-ingång (eller föregående moduls IN)
- **S88n IN**-kontakt → nästa modul i kedjan (lämna tom på den sista modulen)

### Sensorkoppling

**OS-S88n CS — strömavkänning**

![Koppling av strömavkänningsversionen](image.png)

Led spårmatningskablarna för varje detektionssektion genom strömavkänningsingångarna. Varje tåg som drar ström i det avsnittet aktiverar motsvarande ingång.

---

**OS-S88n GND — jordkontakt**

![Koppling av GND-versionen](image-1.png)

Anslut en räls (eller sensorutgång) till en ingångsplintt och den gemensamma räls till COM-plintten. Hjulset som bryggar båda rälsen slutför kretsen till jord och utlöser ingången.

⚠️ *När du använder GND-versionen på en 3-skena-bana är det absolut nödvändigt att kommandostationen och boostrar är av gemensam jord-typ. Om du använder GND-versionen med en H-bryggkommandostation förstör du din kommandostation. Använd OPTO-varianten istället.*

---

**OS-S88n OPTO — optoelektriskt isolerad**

![Koppling av OPTO-versionen](image-3.png)

Anslut sensorns signalutgång till ingångsplintten och sensorns jord till COM-plintten. Ingångsspänningen beror på din sensors matning; kontrollera kortets markeringar för det stödda området.

---

**Seriekoppling av flera moduler**

![Seriekoppling av flera OS-S88n-moduler](image-2.png)

Anslut OUT på varje modul till IN på nästa. Den första modulens OUT går till kommandostationen. Lämna IN-kontakten på den sista modulen i kedjan tom.

---

## Felsökning

**Ingen återkoppling mottagen**
- Kontrollera RJ-45-kablarna och bekräfta att alla 8 ledare är närvarande
- Bekräfta att OUT-kontakten pekar mot kommandostationen (inte IN)
- Verifiera att modulens adressintervall i din programvara stämmer med modulens position i kedjan

**Falska utlösningar**
- GND-version: kontrollera för kabelshortar eller störningar mellan detektionsavsnitt
- CS-version: kontrollera minsta strömförbrukning — LED-enbart vagnar kan behöva ett motstånd för att utlösa detektering
- OPTO-version: kontrollera sensorns matningsspänning och signalpolaritet
- Undvik Ethernet-kablar längre än 5 m

**Fördröjd återkoppling**
- Minska pollingintervallet i din kommandostation eller PC-programvara
- Verifiera korrekt ingångsadressering i din programvara

> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; 🇳🇱 NL &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-S88n Terugmeld­modules Handleiding

**Ondersteunt: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Alle drie OS-S88n module­varianten](all.png)

*Van links naar rechts: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Inleiding

De OS-S88n-modules bieden terugmeld­functionaliteit voor DCC-modelbanen via het gestandaardiseerde S88n-protocol. Met deze modules kunt u blokvrijmelding en baan­gebeurtenissen in real time bewaken, waarbij gegevens naar uw centrale of pc-gestuurd bestuurdings­programma worden gestuurd.

Er zijn drie varianten beschikbaar voor verschillende detectie­behoeften:

- **OS-S88n GND** — massa­contact­detectie, geschikt voor 3-rail (Märklin-stijl) banen
- **OS-S88n CS** — stroom­detectie, geschikt voor 2-rail en 3-rail digitale banen
- **OS-S88n OPTO** — optisch geïsoleerde digitale ingangen, voor gebruik met externe sensoren zoals IR-detectoren of Hall-sensoren

Alle varianten omvatten:

- Doorlus­schakelbare S88n-aansluitingen (RJ-45)
- Schroef­klemmen voor alle sensor­aansluitingen
- Compatibiliteit met alle grote centrales en software (iTrain, Rocrail, Windigipet, enz.)

---

## Module­varianten

### OS-S88n GND — Massa­contact­detectie

![OS-S88n GND module](OS-S88n-GND.png)

De GND-module heeft 16 ingangen die worden geactiveerd wanneer de ingang naar massa wordt getrokken. Compatibele sensoren en detectie­methoden zijn onder andere:

- Rietcontacten
- Drukknopen
- Metalen wielstellen die de rails overbruggen op een 3-rail (Märklin-stijl) baan

⚠️ **Belangrijk — 3-rail banen:** Bij gebruik van de GND-module op een 3-rail baan **moeten** uw centrale en alle versterkers van het gemeenschappelijk massa-type zijn. Als uw centrale een H-brug­uitgang gebruikt, zal het gebruik van de GND-module **uw centrale beschadigen**. Gebruik in dat geval de OPTO-variant.

---

### OS-S88n CS — Stroom­detectie

![OS-S88n CS module](OS-S88n-CS.png)

De CS-module heeft 16 ingangen die worden geactiveerd wanneer er stroom door een bewaakt baan­gedeelte wordt getrokken. Al het rollend materieel dat stroom afneemt, activeert de detectie, waaronder:

- Locomotieven
- Verlichte rijtuigen
- Wagons voorzien van een weerstand voor detectie­doeleinden

Geschikt voor zowel 2-rail als 3-rail digitale banen.

---

### OS-S88n OPTO — Optisch geïsoleerde ingangs­detectie

![OS-S88n OPTO module](OS-S88n-OPTO.png)

De OPTO-module heeft 16 volledig optisch geïsoleerde digitale ingangen. Volledige galvanische isolatie tussen de sensoren en de S88-bus maakt deze variant ideaal voor:

- IR-detectoren
- Hall-sensoren
- Schakelaars op grote afstand van de module
- Gevoelige omgevingen
- Banen waarbij aardlussen of elektrische interferentie een probleem zijn

⚠️ De OPTO-module detecteert **niet** op zichzelf baanvrijmelding — er zijn externe sensoren nodig die een logisch signaal leveren.

---

## Kenmerken

- Volledig compatibel met het S88n-terugmeld­protocol
- RJ-45-aansluitingen voor het in serie schakelen van modules
- 16 ingangen per module
- Tot 31 modules in één keten aansluiten
- Schroef­klemmen voor alle sensor­aansluitingen
- OPTO-versie biedt volledige galvanische isolatie

---

## Modules aansluiten

### Voeding en signaal

Sluit de modules aan op uw centrale via standaard UTP Ethernet-kabels. **Alle 8 draden moeten zijn aangesloten** — vermijd goedkoop gemaakte patchkabels die interne draden weglaten.

- **S88n OUT**-aansluiting → S88n-ingang van de centrale (of de IN van de vorige module)
- **S88n IN**-aansluiting → volgende module in de keten (laat leeg op de laatste module)

### Sensor­bedrading

**OS-S88n CS — stroom­detectie**

![Bedrading van de stroom­detectie versie](image.png)

Leid de baan­voedings­draden voor elke detectie­sectie door de stroom­sensor­ingangen. Een trein die stroom afneemt in die sectie activeert de overeenkomstige ingang.

---

**OS-S88n GND — massa­contact**

![Bedrading van de GND-versie](image-1.png)

Sluit één rail (of sensor­uitgang) aan op een ingangs­klem en de gemeenschappelijke rail op de COM-klem. Wielstellen die beide rails overbruggen sluiten het circuit naar massa en activeren de ingang.

⚠️ *Bij gebruik van de GND-versie op een 3-rail baan is het absoluut noodzakelijk dat de centrale en versterkers van het gemeenschappelijk massa-type zijn. Als u de GND-versie gebruikt met een H-brug­centrale, vernietigt u uw centrale. Gebruik in dat geval de OPTO-variant.*

---

**OS-S88n OPTO — optisch geïsoleerd**

![Bedrading van de OPTO-versie](image-3.png)

Sluit de signaal­uitgang van uw sensor aan op de ingangs­klem en de sensor­massa op de COM-klem. De ingangsspanning hangt af van de voeding van uw sensor; controleer de PCB-markeringen voor het ondersteunde bereik.

---

**Meerdere modules in serie schakelen**

![Meerdere OS-S88n-modules in serie schakelen](image-2.png)

Verbind de OUT van elke module met de IN van de volgende. De OUT van de eerste module gaat naar de centrale. Laat de IN-aansluiting van de laatste module in de keten leeg.

---

## Probleemoplossing

**Geen terugmelding ontvangen**
- Controleer de RJ-45-bedrading en bevestig dat alle 8 geleiders aanwezig zijn
- Bevestig dat de OUT-aansluiting naar de centrale wijst (niet IN)
- Controleer of het adresbereik van de module in uw software overeenkomt met de positie van de module in de keten

**Valse activering**
- GND-versie: controleer op bedradingskort­sluitingen of interferentie tussen detectie­secties
- CS-versie: controleer minimale stroom­afname — wagons met alleen LED-verlichting hebben mogelijk een weerstand nodig om detectie te activeren
- OPTO-versie: controleer sensor­voedings­spanning en signaal­polariteit
- Vermijd Ethernet-kabels langer dan 5 m

**Vertraagde terugmelding**
- Verlaag het poll-interval in uw centrale of pc-software
- Controleer de juiste ingangs­adressering in uw software

> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; 🇩🇪 DE &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-S88n Rückmeldemodule Handbuch

**Unterstützt: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Alle drei OS-S88n-Modulvarianten](all.png)

*Von links nach rechts: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Einführung

Die OS-S88n-Module bieten Rückmeldefunktionalität für DCC-Modelleisenbahnen mithilfe des standardisierten S88n-Protokolls. Diese Module ermöglichen die Echtzeitüberwachung der Gleisbesetzung und von Anlagenereignissen und senden Daten an deine Zentrale oder PC-basierte Steuersoftware.

Drei Varianten sind für unterschiedliche Erkennungsanforderungen erhältlich:

- **OS-S88n GND** — Masseberührungs-Erkennung, geeignet für 3-Leiter-Anlagen (Märklin-Stil)
- **OS-S88n CS** — Stromerkennungs-Erkennung, geeignet für 2-Leiter- und 3-Leiter-Digitalanlagen
- **OS-S88n OPTO** — optisch gekoppelte Digitaleingänge, für externe Sensoren wie IR-Detektoren oder Hall-Sensoren

Alle Varianten beinhalten:

- Verkettbare S88n-Stecker (RJ-45)
- Schraubklemmen für alle Sensoranschlüsse
- Kompatibilität mit allen wichtigen Zentralen und Software (iTrain, Rocrail, Windigipet, usw.)

---

## Modulvarianten

### OS-S88n GND — Masseberührungs-Erkennung

![OS-S88n GND Platine](OS-S88n-GND.png)

Das GND-Modul hat 16 Eingänge, die auslösen, wenn der Eingang auf Masse gezogen wird. Kompatible Sensoren und Erkennungsmethoden umfassen:

- Reedschalter
- Drucktasten
- Metall-Radsätze, die die Schienen einer 3-Leiter-Anlage (Märklin-Stil) überbrücken

⚠️ **Wichtig — 3-Leiter-Anlagen:** Bei Verwendung des GND-Moduls an einer 3-Leiter-Anlage **müssen** Zentrale und alle Booster masseverbundener Bauart sein. Wenn deine Zentrale einen H-Brücken-Ausgang verwendet, **beschädigt** die Verwendung des GND-Moduls deine Zentrale. Verwende in diesem Fall stattdessen die OPTO-Variante.

---

### OS-S88n CS — Stromerkennung

![OS-S88n CS Platine](OS-S88n-CS.png)

Das CS-Modul hat 16 Eingänge, die aktiviert werden, sobald Strom durch einen überwachten Gleisabschnitt fließt. Jedes Rollmaterial, das Strom zieht, löst eine Erkennung aus, einschließlich:

- Lokomotiven
- Beleuchtete Wagen
- Wagen mit eingebautem Widerstand für Erkennungszwecke

Geeignet für 2-Leiter- und 3-Leiter-Digitalanlagen.

---

### OS-S88n OPTO — Optisch entkoppelte Eingangs-Erkennung

![OS-S88n OPTO Platine](OS-S88n-OPTO.png)

Das OPTO-Modul hat 16 vollständig optisch entkoppelte Digitaleingänge. Die vollständige galvanische Trennung zwischen den Sensoren und dem S88-Bus macht diese Variante ideal für:

- IR-Detektoren
- Hall-Sensoren
- Schalter, die weit vom Modul entfernt sind
- Störungsempfindliche Umgebungen
- Anlagen, bei denen Erdschleifen oder elektrische Störungen ein Problem darstellen

⚠️ Das OPTO-Modul erkennt **keine** Gleisbesetzung eigenständig — es benötigt externe Sensoren, die ein Logikpegel-Signal liefern.

---

## Merkmale

- Vollständig kompatibel mit dem S88n-Rückmeldeprotokoll
- RJ-45-Stecker für die Verkettung von Modulen
- 16 Eingänge pro Modul
- Bis zu 31 Module in einer einzelnen Kette stapeln
- Schraubklemmen für alle Sensoranschlüsse
- OPTO-Version bietet vollständige galvanische Trennung

---

## Anschließen der Module

### Strom und Signal

Die Module mithilfe handelsüblicher UTP-Ethernet-Kabel mit der Zentrale verbinden. **Alle 8 Drähte müssen verbunden sein** — billig hergestellte Patchkabel, die interne Drähte weglassen, sind zu vermeiden.

- **S88n OUT**-Stecker → S88n-Eingang der Zentrale (oder IN des vorherigen Moduls)
- **S88n IN**-Stecker → nächstes Modul in der Kette (beim letzten Modul leer lassen)

### Sensorverdrahtung

**OS-S88n CS — Stromerkennung**

![Verdrahtung der Stromerkennung-Version](image.png)

Die Gleiszuleitungsdrähte für jeden Erkennungsabschnitt durch die Stromerkennungseingänge führen. Jeder Zug, der in diesem Abschnitt Strom zieht, aktiviert den entsprechenden Eingang.

---

**OS-S88n GND — Masseberührung**

![Verdrahtung der GND-Version](image-1.png)

Eine Schiene (oder Sensorausgang) an einen Eingangsklemme anschließen und die gemeinsame Schiene an die COM-Klemme. Radsätze, die beide Schienen überbrücken, schließen den Stromkreis zur Masse und lösen den Eingang aus.

⚠️ *Bei Verwendung der GND-Version an einer 3-Leiter-Anlage ist es unbedingt erforderlich, dass Zentrale und Booster masseverbundener Bauart sind. Bei Verwendung der GND-Version mit einer H-Brücken-Zentrale wird die Zentrale zerstört. Verwende stattdessen die OPTO-Variante.*

---

**OS-S88n OPTO — optisch entkoppelt**

![Verdrahtung der OPTO-Version](image-3.png)

Den Signalausgang des Sensors an die Eingangsklemme anschließen und die Sensormasse an die COM-Klemme. Die Eingangsspannung hängt von der Versorgung des Sensors ab; die Platinenbeschriftung für den unterstützten Bereich prüfen.

---

**Verketten mehrerer Module**

![Verkettung mehrerer OS-S88n-Module](image-2.png)

Den OUT jedes Moduls mit dem IN des nächsten verbinden. Der OUT des ersten Moduls geht zur Zentrale. Den IN-Stecker des letzten Moduls in der Kette leer lassen.

---

## Fehlerbehebung

**Keine Rückmeldung erhalten**
- RJ-45-Kabel prüfen und sicherstellen, dass alle 8 Leiter vorhanden sind
- Bestätigen, dass der OUT-Stecker zur Zentrale führt (nicht IN)
- Den Moduladressbereich in der Software mit der Position des Moduls in der Kette abgleichen

**Falsche Auslösungen**
- GND-Version: auf Verdrahtungskurzschlüsse oder Störungen zwischen Erkennungsabschnitten prüfen
- CS-Version: minimalen Stromverbrauch prüfen — reine LED-Wagen benötigen möglicherweise einen Widerstand zur Auslösung der Erkennung
- OPTO-Version: Sensor-Versorgungsspannung und Signalpolarität prüfen
- Ethernet-Kabel länger als 5 m vermeiden

**Verzögerte Rückmeldung**
- Das Abfrageintervall in der Zentrale oder PC-Software verringern
- Korrekte Eingangsadressierung in der Software überprüfen

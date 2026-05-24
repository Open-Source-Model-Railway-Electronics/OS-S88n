> 🌐 &nbsp; 🇬🇧 EN &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-S88n Feedback Modules Manual

**Supports: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![All three OS-S88n module variants](all.png)

*Left to right: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introduction

The OS-S88n modules provide feedback functionality for DCC model railroads using the standardized S88n protocol. These modules allow real-time monitoring of block occupancy and layout events, sending data to your command station or PC-based control software.

Three variants are available to suit different detection needs:

- **OS-S88n GND** — ground-contact detection, suitable for 3-rail (Märklin-style) layouts
- **OS-S88n CS** — current-sensing detection, suitable for 2-rail and 3-rail digital layouts
- **OS-S88n OPTO** — opto-isolated digital inputs, for use with external sensors such as IR detectors or Hall sensors

All variants include:

- Daisy-chainable S88n connectors (RJ-45)
- Screw terminals for all sensor connections
- Compatibility with all major command stations and software (iTrain, Rocrail, Windigipet, etc.)

---

## Module Variants

### OS-S88n GND — Ground Contact Detection

![OS-S88n GND board](OS-S88n-GND.png)

The GND module has 16 inputs that trigger when the input is pulled to ground. Compatible sensors and detection methods include:

- Reed switches
- Push buttons
- Metal wheelsets bridging the rails on a 3-rail (Märklin-style) layout

⚠️ **Important — 3-rail layouts:** When using the GND module on a 3-rail layout, your command station and all boosters **must** be common-ground type. If your command station uses an H-bridge output, using the GND module **will damage your command station**. Use the OPTO variant instead in that case.

---

### OS-S88n CS — Current Sensing

![OS-S88n CS board](OS-S88n-CS.png)

The CS module has 16 inputs that activate whenever current is drawn through a monitored track section. Any rolling stock that draws current will trigger detection, including:

- Locomotives
- Lighted coaches
- Wagons fitted with a resistor for detection purposes

Suitable for both 2-rail and 3-rail digital layouts.

---

### OS-S88n OPTO — Opto-Isolated Input Detection

![OS-S88n OPTO board](OS-S88n-OPTO.png)

The OPTO module has 16 fully opto-isolated digital inputs. Full galvanic isolation between the sensors and the S88 bus makes this variant ideal for:

- IR detectors
- Hall sensors
- Switches located far from the module
- Noise-sensitive environments
- Layouts where ground loops or electrical interference are a concern

⚠️ The OPTO module does **not** detect track occupancy by itself — it requires external sensors that provide a logic-level signal.

---

## Features

- Fully compatible with the S88n feedback protocol
- RJ-45 connectors for daisy-chaining modules
- 16 inputs per module
- Stack up to 31 modules in a single chain
- Screw terminals for all sensor connections
- OPTO version provides full galvanic isolation

---

## Connecting the Modules

### Power and Signal

Connect the modules to your command station using standard UTP Ethernet cables. **All 8 wires must be connected** — avoid cheaply made patch cables that omit internal wires.

- **S88n OUT** connector → command station S88n input (or the previous module's IN)
- **S88n IN** connector → next module in the chain (leave empty on the last module)

### Sensor Wiring

**OS-S88n CS — current sensing**

![Wiring of the Current Sense version](image.png)

Route the track feed wires for each detection section through the current sensor inputs. Any train drawing current in that section activates the corresponding input.

---

**OS-S88n GND — ground contact**

![Wiring of the GND version](image-1.png)

Connect one rail (or sensor output) to an input terminal and the common rail to the COM terminal. Wheelsets bridging both rails complete the circuit to ground and trigger the input.

⚠️ *When using the GND version on a 3-rail layout, it is imperative that the command station and boosters are common-ground type. If you use the GND version with an H-bridge command station, you will destroy your command station. Use the OPTO variant instead.*

---

**OS-S88n OPTO — opto-isolated**

![Wiring of the OPTO version](image-3.png)

Connect your sensor's signal output to the input terminal and the sensor ground to the COM terminal. The input voltage depends on your sensor's supply; check the board markings for the supported range.

---

**Daisy-chaining multiple modules**

![Daisy-chaining several OS-S88n modules](image-2.png)

Connect the OUT of each module to the IN of the next. The first module's OUT goes to the command station. Leave the IN connector of the last module in the chain empty.

---

## Troubleshooting

**No feedback received**
- Check RJ-45 cabling and confirm all 8 conductors are present
- Confirm the OUT connector goes toward the command station (not IN)
- Verify the module address range in your software matches the module's position in the chain

**False triggers**
- GND version: check for wiring shorts or interference between detection sections
- CS version: check minimum current draw — LED-only wagons may need a resistor to trigger detection
- OPTO version: check sensor supply voltage and signal polarity
- Avoid Ethernet cables longer than 5 m

**Delayed feedback**
- Reduce the polling interval in your command station or PC software
- Verify correct input addressing in your software

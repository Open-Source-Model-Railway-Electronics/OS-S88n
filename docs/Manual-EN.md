# OS-S88n Feedback Modules Manual
Supports: OS-S88n GND, OS-S88n CS

## 📘 Introduction
The OS-S88n modules provide feedback functionality for DCC model railroads using the standardized S88n protocol. These modules allow real-time monitoring of block occupancy and layout events by sending data to your command station or PC-based software.
Models:
    • OS-S88n GND — Standard input module using ground-contact detection
    • OS-S88n CS — Enhanced current-sensing module
Both versions include:
    • Daisy-chainable S88n connectors (RJ-45)
    • Screw terminals for simple input wiring
    • Compatibility with major command stations and software (e.g., iTrain, Rocrail, Windigipet, etc.)

---

## 📚 Table of Contents
    1. 📘 Introduction
    2. ⚖️ Module Variants: GND vs CS
    3. 🔧 Features
    4. 🔌 Connecting the OS-S88n Modules
    5. ⚡ Troubleshooting

---

## ⚖️ Module Variants: GND vs CS
🟡 OS-S88n GND
    • 16 digital inputs using contact-to-ground detection
    • Compatible with:
        ◦ Reed switches
        ◦ Push buttons
        ◦ Axle-based contact detection (e.g., metal wheelsets bridging rails)
    • COM terminal must be connected to the J line of the track (commonly used as the ground reference)
    • ⚠️ This variant is especially well-suited for 3-rail systems such as Märklin, where axle bridges between center studs and outer rails are common.
🟢 OS-S88n CS
    • 16 inputs using current-sensing detection
    • Detects the flow of current through a connected block
    • Ideal for:
        ◦ Lighted cars
        ◦ Locomotives
        ◦ Rolling stock with power draw
    • COM terminal must be connected to the K line of the track — typically the rail opposite

---

## 🔧 Features
    • Fully compatible with the S88n feedback protocol
    • RJ-45 connectors for signal daisy-chaining
    • Supports up to 16 inputs per module
    • Stack up to 31 modules in a chain
    • Screw terminals for hassle-free wiring

---

## 🔌 Connecting the OS-S88n Modules
Power and Signal
    • S88n OUT connects to the command station or previous module
    • S88n IN connects to the next module (leave empty on the last module)
    • Use standard Ethernet cables (with all 8 wires connected)
⚠️ Note: Some cheap Ethernet cables lack some internal conductors — always use full-wire cables

Sensor Wiring
OS-S88n GND
    • Connect sensor/device to one of the 16 input terminals
    • Connect COM to the J line of the track
    • A conductive axle or external switch pulling the input to J will trigger detection
    • ⚠️ Especially useful in 3-rail Märklin-style systems, where grounding is reliably available via center-stud contact
OS-S88n CS
    • Each input monitors current via internal current sensors
    • COM must be connected to the K line of the track
    • Any car or loco that draws even a small current activates the input
⚠️ Be sure to separate track sections (blocks) so each one feeds one current-sensing input

![](image.png)

![](image-1.png)

![](image-2.png)

---

## ⚡ Troubleshooting
    • No feedback received?
        ◦ Check RJ-45 cables
        ◦ Ensure all 8 wires are present
        ◦ Confirm OUT is going to the command station
    • False triggers?
        ◦ For GND modules: check for noise or interference near track wiring
        ◦ For CS modules: ensure current draw is sufficient (LED cars might need a resistor)
        ◦ Avoid overly long Ethernet cables (>5m)
    • Delayed feedback?
        ◦ Reduce the polling interval in your command station or software
        ◦ Ensure correct address mapping

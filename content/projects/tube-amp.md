---
title: "Tube Amplifier Build"
status: "growing"
weight: 3
---

This project is on the backburner a bit, working on the DAP right now.

A single-ended tube amplifier built from scratch. Point-to-point wiring, no PCB. The kind of thing you build because you want to understand every electron's path from source to speaker.

Here is my current BOM

Power Transformer

T1: Hammond 372BX

Primaries: Dual 120VAC (parallel for 120V operation)
HV Secondary: 300-0-300VAC @ 100mA
Heater 1: 6.3V CT @ 3A
Heater 2: 5V CT @ 2A
Part Number: 166-372BX
Price: ~$95




B+ Supply Components
Rectifier

V1: 5AR4/GZ34 tube rectifier

Rating: 250mA max
Options: Shuguang ($30) or NOS Mullard/Telefunken ($80+)
Socket: 8-pin octal ceramic (Belton VT8-PT-S, $8)



Filter Components

C1: 220µF 450V electrolytic

Part: Nichicon LKG2W221MESZ
Price: ~$8


L1: Hammond 193J choke

Value: 5H @ 100mA
DCR: 300Ω
Price: ~$28


C2: 470µF 450V electrolytic

Part: Nichicon LKG2W471MESY
Price: ~$10



Voltage Dropper

R_B+: 1.5kΩ 10W wire-wound resistor

Part: Ohmite 270-1K5
Price: ~$3




DC Heater Supply Components
Rectification

BR1: W04M bridge rectifier

Rating: 400V 1.5A
Price: ~$0.50



Pre-Dropper

R_drop: 4.7Ω 15W wire-wound resistor

Part: Ohmite 270-4R7
Price: ~$3



Filtering (Pre-Regulator)

C7: 4700µF 25V electrolytic

Part: Panasonic ECA-1EM472
Price: ~$3



Voltage Regulator

U1: LM338T adjustable regulator

Package: TO-220
Rating: 5A
Part: TI LM338T/NOPB
Price: ~$3


R5: 270Ω 1% 1/4W metal film (ADJ to GND)

Part: Vishay MBB0207C2700FC
Price: ~$0.25


R6: 1.1kΩ 1% 1/4W metal film (ADJ to OUT)

Part: Vishay MBB0207C1101FC
Price: ~$0.25


HS1: Heatsink for LM338

Thermal resistance: ≤7°C/W
Part: Aavid 577102B00
Price: ~$5



Output Filtering

C8: 10,000µF 16V low-ESR electrolytic

Part: Panasonic EEU-FM1C103
ESR: <0.05Ω
Price: ~$5


C9: 0.1µF 50V ceramic (X7R)

Generic part
Price: ~$0.10




Distribution Hardware
Tag Strips

TS1: Positive heater bus (5-position turret)

Part: Keystone 1311
Price: ~$2


TS2: Ground heater bus (5-position turret)

Part: Keystone 1311
Price: ~$2



Wiring

Bus wire: 18AWG bare tinned copper

For tag strip buses and B+ distribution
Price: ~$2


Hookup wire: 22AWG stranded (red/black)

For tube heater connections
Price: ~$3




AC Mains Components

F1: 1A slow-blow fuse

Rating: 250VAC
Part: Littelfuse 313 series
Price: ~$1


SW1: Power switch

Type: SPST toggle
Rating: 125VAC 10A
Price: ~$3


Power cord: 3-wire grounded (18AWG)

Price: ~$5




Grounding & Mounting Hardware

Star ground lug: Brass lug, 1/4" bolt

Price: ~$2


Ceramic standoffs: For mounting resistors, tag strips

Price: ~$5


Capacitor clamps: For tall electrolytic caps

Price: ~$1 each (×4 = $4)


Solder lugs, terminals: Assorted

Price: ~$5

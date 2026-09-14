# Analog Layout Course

Coursework and practice in CMOS transistor characterization, schematic design, simulation, and IC layout using SKY130, Xschem, ngspice, and KLayout.

## Labs

### Lab 01 — NMOS & PMOS Characterization
Basic MOSFET characterization and simulation:
- DC operating point
- I–V characteristics
- Threshold behavior
- Transconductance `gm`
- Output resistance `ro`
- Operating regions

Directory: [`lab01-nmos-pmos`](./lab01-nmos-pmos)

### Lab 02 — CMOS Logic Gates: Schematic to Layout
CMOS logic-gate design flow from transistor-level schematic to physical layout:

`Boolean function → CMOS network → Xschem schematic → simulation → KLayout layout → DRC/LVS`

Directory: [`lab02-cmos-logic-gates`](./lab02-cmos-logic-gates)

## Tools

- SKY130 PDK
- Xschem
- ngspice
- KLayout

## Repository Structure

```text
analog-layout-course/
├── README.md
├── lab01-nmos-pmos/
│   ├── README.md
│   ├── schematic/
│   ├── simulation/
│   └── results/
└── lab02-cmos-logic-gates/
    ├── README.md
    ├── inverter/
    ├── nand2/
    ├── nor2/
    └── other-gates/
```

# Analog Layout Course

Coursework and practice in CMOS transistor characterization, schematic design, simulation, and IC layout using SKY130, IHP SG13G2, Xschem, ngspice, and KLayout.

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

### Lab 03 — Common-Source Stage
Design and simulation of a CMOS common-source amplifier with a PMOS current-source load using IHP SG13G2.

Main design targets:
- `VDD = 1.2 V`
- `CL = 100 fF`
- Gain `>= 30 dB`
- `0.4 V <= Vout <= 0.8 V`
- Power `< 0.5 mW`

Final simulated result: approximately `30.04 dB` gain, `0.600 V` DC output, `45.35 uW` power, and `11.44 MHz` bandwidth.

Directory: [`lab03-common-source-stage`](./lab03-common-source-stage)

## Tools

- SKY130 PDK
- IHP SG13G2 PDK
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
├── lab02-cmos-logic-gates/
│   ├── README.md
│   ├── inverter/
│   ├── nand2/
│   ├── nor2/
│   └── other-gates/
└── lab03-common-source-stage/
    ├── README.md
    └── simulation/
        └── cs_amplifier.spice
```

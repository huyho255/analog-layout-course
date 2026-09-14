# Lab 02 — CMOS Logic Gates: Schematic to Layout

## Objective

Design CMOS logic gates from transistor-level schematic through simulation and physical layout.

## Design Flow

`Boolean function → CMOS transistor network → Xschem schematic → ngspice simulation → KLayout layout → DRC/LVS`

## Initial Gates

- Inverter
- 2-input NAND
- 2-input NOR
- Additional gates as required

## Suggested Structure

```text
lab02-cmos-logic-gates/
├── README.md
├── inverter/
├── nand2/
├── nor2/
└── other-gates/
```

For each gate, keep the schematic, testbench/simulation results, layout, and screenshots together so the full schematic-to-layout flow is easy to review.

# Lab 03 — Common-Source Stage

Lab 03 contains **two exercises** from the common-source-stage lecture.

## Exercise 01 — Common-Source Stages

Recreate the lecture examples:

1. Common-source amplifier with a resistor load.
2. Common-source amplifier with a diode-connected MOS load.
3. Create the required Xschem symbols for the circuits.

Directory: [`exercise01-basic-common-source`](./exercise01-basic-common-source)

## Exercise 02 — Common-Source Amplifier Design

Design a common-source amplifier using the IHP SG13G2 PDK with these targets:

- `VDD = 1.2 V`
- `CL = 100 fF`
- Gain `>= 30 dB`
- `0.4 V <= Vout,DC <= 0.8 V`
- Power `< 0.5 mW`

The final design currently uses:

```text
M1: W = 10 um, L = 3.2 um
M2: W = 10 um, L = 3.2 um
VIN,DC = 0.45 V
VBIAS = 0.2966127 V
```

Simulation result:

```text
Vout ~= 0.600 V
Gain ~= 30.04 dB
Power ~= 45.35 uW
f3dB ~= 11.44 MHz
```

The Exercise 02 folder also contains the hand calculations, saturation checks, output-resistance calculation, and gain-bandwidth discussion.

Directory: [`exercise02-design-target`](./exercise02-design-target)

## Structure

```text
lab03-common-source-stage/
├── README.md
├── exercise01-basic-common-source/
│   └── README.md
└── exercise02-design-target/
    ├── README.md
    └── simulation/
        └── cs_amplifier.spice
```

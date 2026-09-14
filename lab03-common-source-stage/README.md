# Lab 03 — Common-Source Stage

Design and simulation of a CMOS common-source amplifier using the IHP SG13G2 PDK, Xschem, and ngspice.

## Design Specifications

- Supply voltage: `VDD = 1.2 V`
- Load capacitance: `CL = 100 fF`
- Required voltage gain: `Av >= 30 dB`
- DC output voltage: `0.4 V <= Vout <= 0.8 V`
- Power consumption: `< 0.5 mW`

## Final Design

| Parameter | Value |
|---|---:|
| NMOS M1 | `W = 10 um`, `L = 3.2 um` |
| PMOS M2 | `W = 10 um`, `L = 3.2 um` |
| `VIN,DC` | `0.45 V` |
| `VBIAS` | `0.2966127 V` |
| `VDD` | `1.2 V` |
| `CL` | `100 fF` |

M1 is the common-source NMOS transistor. M2 is used as a PMOS current-source load.

## Small-Signal Gain

For the common-source stage with a PMOS current-source load,

```text
Av = -gm1(ro1 || ro2)
```

From the ngspice operating point:

```text
gm1  = 276.193 uS
gds1 = 6.22849 uS
gds2 = 2.46283 uS
```

Therefore,

```text
ro1 = 1/gds1 = 160.55 kohm
ro2 = 1/gds2 = 406.04 kohm
```

The output resistance is

```text
Rout = ro1 || ro2
     = 115.06 kohm
```

The hand-calculated voltage gain is

```text
Av = -(276.193 uS)(115.06 kohm)
   = -31.78 V/V
```

Converting to decibels,

```text
Av,dB = 20 log10(|Av|)
      = 30.043 dB
```

The negative sign indicates the 180-degree phase inversion of a common-source amplifier.

## Saturation Check

### NMOS M1

```text
VGS1 = 0.45 V
VTH1 = 0.1864 V
VOV1 = VGS1 - VTH1
     = 0.2636 V

VDS1 ~= 0.600 V
```

Since

```text
VDS1 > VOV1
```

M1 operates in saturation.

### PMOS M2

```text
VSG2 = VDD - VBIAS
     = 1.2 - 0.2966127
     = 0.9033873 V

|VTH2| = 0.3481 V
VOV2 = VSG2 - |VTH2|
     = 0.5553 V

VSD2 = VDD - VOUT
     ~= 0.600 V
```

Since

```text
VSD2 > VOV2
```

M2 also operates in saturation.

## Power Consumption

The simulated supply current is approximately

```text
IDD = 37.79 uA
```

Thus,

```text
P = VDD * IDD
  = 1.2 * 37.79 uA
  = 45.35 uW
```

This is well below the `0.5 mW` specification.

## AC Simulation Results

| Quantity | Result |
|---|---:|
| `Vout,DC` | `0.59995 V` |
| Low-frequency gain | `30.0425 dB` |
| Linear gain | `~31.78 V/V` |
| Power | `45.35 uW` |
| `f3dB` | `~11.44 MHz` |

The simulated gain is almost identical to the hand calculation:

```text
Hand calculation : 30.043 dB
Simulation       : 30.0425 dB
```

## Bandwidth Estimate

Using the dominant-output-pole approximation,

```text
f3dB ~= 1 / (2*pi*Rout*CL)
```

with

```text
Rout = 115.06 kohm
CL   = 100 fF
```

gives

```text
f3dB,hand ~= 13.83 MHz
```

Ngspice gives approximately

```text
f3dB,sim ~= 11.44 MHz
```

The simulated bandwidth is lower because the MOS devices add parasitic capacitances such as `Cgd`, `Cdb`, and `Cgs` in addition to the external load capacitance.

## Gain–Bandwidth Trade-off

Increasing transistor channel length generally increases output resistance. A larger `Rout` increases the voltage gain because

```text
|Av| = gm1 * Rout
```

but it also lowers the output pole:

```text
fp ~= 1 / (2*pi*Rout*Cout)
```

Therefore, increasing `Rout` improves gain but reduces bandwidth. The final `L = 3.2 um` design was selected to obtain slightly more than `30 dB` gain while maintaining a bandwidth of about `11.44 MHz`.

## Simulation

The final ngspice control block used in Xschem is available in [`simulation/cs_amplifier.spice`](./simulation/cs_amplifier.spice).

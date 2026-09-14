# Exercise 02 — Common-Source Amplifier Design Target

## Specifications

- `VDD = 1.2 V`
- `CL = 100 fF`
- Voltage gain `>= 30 dB`
- `0.4 V <= Vout,DC <= 0.8 V`
- Power consumption `< 0.5 mW`

Use

```text
Av = -gm1(ro1 || ro2)
```

## Final design

| Parameter | Value |
|---|---:|
| M1 NMOS | `W = 10 um`, `L = 3.2 um` |
| M2 PMOS | `W = 10 um`, `L = 3.2 um` |
| `VIN,DC` | `0.45 V` |
| `VBIAS` | `0.2966127 V` |
| `VDD` | `1.2 V` |
| `CL` | `100 fF` |

## Operating-point data

```text
gm1  = 276.193 uS
gds1 = 6.22849 uS
gds2 = 2.46283 uS
IDD   = 37.79 uA
Vout  = 0.59995 V
```

## Hand calculation

```text
ro1 = 1/gds1 = 160.55 kohm
ro2 = 1/gds2 = 406.04 kohm
Rout = ro1 || ro2 = 115.06 kohm

Av = -gm1*Rout
   = -31.78 V/V

Av,dB = 20log10(|Av|)
      = 30.043 dB
```

## Saturation check

For M1:

```text
VGS1 = 0.45 V
VTH1 = 0.1864 V
VOV1 = 0.2636 V
VDS1 ~= 0.600 V
```

Since `VDS1 > VOV1`, M1 is in saturation.

For M2:

```text
VSG2 = 1.2 - 0.2966127 = 0.9033873 V
|VTH2| ~= 0.3481 V
VOV2 ~= 0.5553 V
VSD2 ~= 0.600 V
```

Since `VSD2 > VOV2`, M2 is also in saturation.

## Power

```text
P = VDD*IDD
  = 1.2*37.79 uA
  = 45.35 uW
```

This satisfies the `< 0.5 mW` requirement.

## Simulation results

| Quantity | Result |
|---|---:|
| `Vout,DC` | `0.59995 V` |
| Low-frequency gain | `30.0425 dB` |
| Linear gain | `~31.78 V/V` |
| Power | `45.35 uW` |
| `f3dB` | `~11.44 MHz` |

## Bandwidth estimate

Using

```text
f3dB ~= 1/(2*pi*Rout*CL)
```

gives approximately `13.83 MHz` by hand, while ngspice gives about `11.44 MHz`. The difference is caused by transistor parasitic capacitances in addition to the external `100 fF` load.

## Simulation file

See [`simulation/cs_amplifier.spice`](./simulation/cs_amplifier.spice).

# Lab 01 — NMOS & PMOS Characterization

This lab analyzes NMOS and PMOS devices using Xschem and ngspice. The report uses `sg13_lv_nmos` and `sg13_lv_pmos` devices with `W = 0.15 µm` and `L = 0.13 µm`.

## NMOS

### Setup

The NMOS testbench biases both `VGS` and `VDS` up to 1.2 V and performs an operating-point analysis plus a nested DC sweep.

```spice
XM1 VDS VGS 0 0 sg13_lv_nmos w=0.15u l=0.13u ng=1 m=1 mm_ok=1
VGS VGS 0 1.2
VDS VDS 0 1.2

.lib cornerMOSlv.lib mos_tt
.param temp=27
.control
save all
op
dc VDS 0 1.2 0.1 VGS 0 1.2 0.1
```

The extracted device quantities are:

```spice
let vgs = @n.xm1.nsg13_lv_nmos[vgs]
let vds = @n.xm1.nsg13_lv_nmos[vds]
let vth = @n.xm1.nsg13_lv_nmos[vth]
let ro  = 1/@n.xm1.nsg13_lv_nmos[gds]
let gm  = @n.xm1.nsg13_lv_nmos[gm]
let av_ins_db = db(gm*ro)
```

### Operating point

| Parameter | Value |
|---|---:|
| `VGS` | 1.2 V |
| `VDS` | 1.2 V |
| `VTH` | 0.4424 V |
| `ro` | 87.315 kΩ |
| `gm` | 143.198 µS |
| Intrinsic gain | 21.94 dB |

### DC characteristics

The report includes:

- `ID–VGS` transfer characteristics
- `ID–VDS` output characteristics for multiple gate-bias values

## PMOS

### Setup

The PMOS testbench uses `VSG = 1.2 V` and `VSD = 1.2 V` for the operating point. The report performs a DC sweep of `VSG` from 0 to 1.2 V.

```spice
VSG net1 net2 1.2
VSD net1 0 1.2
XM1 0 net2 net1 net1 sg13_lv_pmos w=0.15u l=0.13u ng=1 m=1 mm_ok=1

.lib cornerMOSlv.lib mos_tt
.param temp=27
.control
save all
op
dc VSG 0 1.2 0.01
```

The extracted device quantities are:

```spice
let vgs = @n.xm1.nsg13_lv_pmos[vgs]
let vds = @n.xm1.nsg13_lv_pmos[vds]
let vth = @n.xm1.nsg13_lv_pmos[vth]
let ro  = 1/@n.xm1.nsg13_lv_pmos[gds]
let gm  = @n.xm1.nsg13_lv_pmos[gm]
let av_ins_db = db(gm*ro)
```

### Operating point

| Parameter | Value |
|---|---:|
| `VSG` | 1.2 V |
| `VSD` | 1.2 V |
| `VTH` | 0.4225 V |
| `ro` | 145.13 kΩ |
| `gm` | 101.81 µS |
| Intrinsic gain | 23.39 dB |

### DC characteristics

The report includes:

- `ID–VGS` transfer characteristics
- `ID–VDS` output characteristics

## Tools

- Xschem
- ngspice
- IHP SG13G2 low-voltage MOS models

## Files

```text
lab01-nmos-pmos/
├── README.md
└── results/
    └── README.md
```

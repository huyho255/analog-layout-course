# Ex2
## Common-Source NMOS with PMOS Active Load  — Hand Calculation

The circuit consists of:

- **M1:** NMOS common-source transistor
- **M2:** PMOS active-load transistor
- Supply voltage:  
  \[
  V_{DD}=1.2\text{ V}
  \]

Target specifications from the hand calculation:

- Voltage gain:
  \[
  |A_v| \ge 30\text{ dB}
  \]
- Output voltage range:
  \[
  V_{out}\approx 0.4\text{ V} \rightarrow 0.8\text{ V}
  \]
- Power:
  \[
  P<0.5\text{ mW}
  \]

For small-signal operation,

\[
A_v \approx -g_{m1}(r_{o1}\parallel r_{o2})
\]

---

## 2. Choose the DC output voltage

Choose

\[
V_{out}=V_{DS1}=0.7\text{ V}
\]

For transistor \(M_2\),

\[
V_{SD2}=V_{DD}-V_{out}
\]

Therefore,

\[
V_{SD2}=1.2-0.7=0.5\text{ V}
\]

---

## 3. PMOS overdrive voltage

For \(M_2\),

\[
V_{OV2}=V_{SG2}-|V_{TH2}|
\]

and

\[
V_{SG2}=V_{DD}-V_B
\]

Hence,

\[
V_{OV2}=V_{DD}-V_B-|V_{TH2}|
\]

Using approximately

\[
|V_{TH2}|\approx0.33\text{ V}
\]

gives

\[
V_{OV2}=1.2-V_B-0.33
\]

To keep \(M_2\) in saturation,

\[
V_{SD2}\ge V_{OV2}
\]

so

\[
0.5 \ge 1.2-V_B-0.33
\]

\[
V_B\gtrsim0.37\text{ V}
\]

A convenient choice from the hand calculation is approximately

\[
V_B\approx0.38\text{ V}
\]

which gives

\[
V_{OV2}\approx0.49\text{ V}
\]

> Note: The handwritten value around this step is slightly unclear, so the exact \(V_B\) value should be checked against the SPICE model.

---

## 4. NMOS saturation condition

For \(M_1\),

\[
V_{DS1}\ge V_{OV1}
\]

Since

\[
V_{DS1}=V_{out}=0.7\text{ V}
\]

and

\[
V_{OV1}=V_{GS1}-V_{TH1}=V_{in}-V_{TH1}
\]

the saturation condition becomes

\[
0.7\ge V_{in}-V_{TH1}
\]

Assuming

\[
V_{TH1}\approx0.25\text{ V}
\]

then

\[
V_{in}\le0.7+0.25=0.95\text{ V}
\]

---

## 5. Output resistance

Using channel-length modulation,

\[
r_o=\frac{1}{\lambda I_D}
\]

From the handwritten notes, the estimated output resistances are approximately on the order of

\[
r_{o1},r_{o2}\sim100\text{ k}\Omega
\]

and therefore

\[
r_{o1}\parallel r_{o2}
\]

is used in the gain calculation.

---

## 6. Gain requirement

The voltage gain is approximated by

\[
A_v=-g_{m1}(r_{o1}\parallel r_{o2})
\]

The target gain is

\[
|A_v|\ge30\text{ dB}
\]

Convert dB to linear gain:

\[
|A_v|\ge10^{30/20}
\]

\[
|A_v|\ge31.62
\]

Thus,

\[
g_{m1}(r_{o1}\parallel r_{o2})\ge31.62
\]

---

## 7. Drain current and power

From the handwritten calculation,

\[
I_D\approx23.9\ \mu\text{A}
\]

Therefore the DC power is

\[
P=I_DV_{DD}
\]

\[
P\approx23.9\ \mu\text{A}\times1.2\text{ V}
\]

\[
P\approx28.7\ \mu\text{W}
\]

which satisfies

\[
P<0.5\text{ mW}
\]

---

## 8. PMOS sizing

For a PMOS in saturation,

\[
I_D=
\frac{1}{2}
\left(\frac{W}{L}\right)_2
\mu_p C_{ox}
V_{OV2}^2
\]

Solving for the aspect ratio,

\[
\left(\frac{W}{L}\right)_2
=
\frac{2I_D}
{\mu_pC_{ox}V_{OV2}^2}
\]

Using the values from the hand calculation gives approximately

\[
\boxed{
\left(\frac{W}{L}\right)_2\approx0.208
}
\]

---

## 9. NMOS sizing

For the NMOS,

\[
I_D=
\frac{1}{2}
\left(\frac{W}{L}\right)_1
\mu_n C_{ox}
V_{OV1}^2
\]

Thus,

\[
\left(\frac{W}{L}\right)_1
=
\frac{2I_D}
{\mu_nC_{ox}V_{OV1}^2}
\]

From the handwritten calculation,

\[
\boxed{
\left(\frac{W}{L}\right)_1\approx0.38
}
\]

---

## 10. Preliminary design values

| Parameter | Approximate value |
|---|---:|
| \(V_{DD}\) | \(1.2\text{ V}\) |
| \(V_{out,Q}\) | \(0.7\text{ V}\) |
| \(V_{SD2}\) | \(0.5\text{ V}\) |
| \(V_B\) | \(\approx0.38\text{ V}\) |
| \(I_D\) | \(\approx23.9\ \mu\text{A}\) |
| Power | \(\approx28.7\ \mu\text{W}\) |
| Target gain | \(\ge30\text{ dB}\) |
| \((W/L)_1\) | \(\approx0.38\) |
| \((W/L)_2\) | \(\approx0.208\) |

---

## 11. Equations used

### MOSFET overdrive voltage

For NMOS:

\[
V_{OV}=V_{GS}-V_{TH}
\]

For PMOS:

\[
V_{OV}=V_{SG}-|V_{TH}|
\]

### Saturation conditions

NMOS:

\[
V_{DS}\ge V_{OV}
\]

PMOS:

\[
V_{SD}\ge V_{OV}
\]

### Drain current

\[
I_D=
\frac{1}{2}
\mu C_{ox}
\frac{W}{L}
V_{OV}^2
\]

### Output resistance

\[
r_o=\frac{1}{\lambda I_D}
\]

### Common-source voltage gain

\[
A_v\approx-g_m(r_{o1}\parallel r_{o2})
\]

### Power

\[
P=V_{DD}I_D
\]

---

## 12. Notes

These calculations are intended as a **first-pass hand design**.  
The final transistor dimensions and bias voltages should be refined using SPICE simulation with the actual NMOS/PMOS model parameters:

- \(V_{TH}\)
- \(\mu_n C_{ox}\)
- \(\mu_p C_{ox}\)
- \(\lambda_n\)
- \(\lambda_p\)

After sizing, verify:

1. DC operating point
2. Saturation region of both MOSFETs
3. Small-signal voltage gain
4. Output swing
5. Power consumption
6. AC bandwidth


# Experiment 2: Source Degenerated CS Amplifier Variations

**Simulation Tool:** LTspice  
**Technology:** TSMC 180nm CMOS  
**Supply Voltage:** 1.8 V  
**Load Capacitance:** 1 pF  

---

# Aim

To design and simulate three variations of a Common-Source (CS) amplifier with source degeneration and compare their:

- DC bias behavior  
- Gain  
- Linearity  
- Bandwidth  
- Power consumption  

---

# Circuits Implemented

1. Resistive Source Degeneration (Rs)
2. MOS Source Degeneration (Fixed VBN)
3. Gate-Tied MOS Degeneration (Self Bias)

---

# Resistive Source Degenerated CS Amplifier

---

## Circuit Diagram


<img width="1037" height="767" alt="cktdgm1" src="https://github.com/user-attachments/assets/9df03e4a-5ea0-4c25-ab5a-629ca02bd01a" />



---

## Components Used

| Component | Value |
|-----------|--------|
| M1 (NMOS) | W = 390 nm, L = 180 nm |
| M2 (PMOS) | W = 1.5 µm, L = 180 nm |
| Rs | 15 kΩ |
| VDD | 1.8 V |
| VBP | 1.21 V |
| CL | 1 pF |

---

## Procedure

### Step 1: DC Operating Point

1. Place `.op` command.
2. Run simulation.
3. Note ID, Vout, VGS, VDS.
4. Verify M1 operates in saturation.


<img width="850" height="633" alt="dcop1" src="https://github.com/user-attachments/assets/082a6050-d347-4813-9130-e4903f05efab" />

---

### Step 2: DC Sweep

```
.dc V2 0 1.8 0.01
```

- Sweep Vin from 0 to 1.8V.
- Select midpoint where:

Vout ≈ VDD / 2 = 0.9V

Selected DC Offset ≈ 0.549 V
#### Varying Resistor,  R :


<img width="1917" height="850" alt="dcsweepvarR1" src="https://github.com/user-attachments/assets/e3927d0d-f07a-458f-87cb-44c6c6e831bd" />

#### Varying Width, W :


<img width="1915" height="850" alt="dcsweepvarW1" src="https://github.com/user-attachments/assets/cd4f7f88-b5f6-41c4-b7ce-f4f78067d53c" />



---

## DC Calculations

Drain current:

ID ≈ 3.5 µA

Power:

P = VDD × ID  
P ≈ 1.8 × 3.5µA  
P ≈ 6.3 µW  

✔ Power < 20 µW

---

## Transient Analysis

Input:

```
SIN(0.549 10m 1k)
```
<img width="1918" height="880" alt="TA1" src="https://github.com/user-attachments/assets/df34d0c5-777c-4603-a7e5-8480a580012b" />


Observations:

- Output inverted (180° phase shift)
- Moderate gain
- Improved linearity

---

## AC Analysis

```
.ac dec 10 100 1G
```
<img width="1908" height="847" alt="AC1" src="https://github.com/user-attachments/assets/b88c7b6a-74b3-4d5a-84c1-89a1f5c30dd0" />


Midband Gain ≈ 18–20 dB  

Linear Gain:

Av = 10^(Gain_dB/20)  
Av ≈ 8 – 10  

Bandwidth moderate.

---

## Inference

- Rs reduces gain.
- Improves linearity.
- Introduces local negative feedback.

---

# MOS Source Degenerated CS (Fixed VBN)

---

## Circuit Diagram

<img width="1170" height="750" alt="cktdgm2" src="https://github.com/user-attachments/assets/10b06689-452e-44a9-b6dc-88c01a53e968" />



---

## Components Used

| Component | Value |
|-----------|--------|
| M1 | W = 390 nm |
| M2 | W = 1.5 µm |
| M3 | W = 180 nm |
| L (All) | 180 nm |
| VBN | 0.55 V |
| VBP | 1.21 V |
| VDD | 1.8 V |
| CL | 1 pF |

---

## Operating Principle

<img width="847" height="635" alt="dcop2" src="https://github.com/user-attachments/assets/d3dbc71e-c4ab-47dd-a2e7-6779b829f68c" />


M3 operates in linear region and behaves as:

Ron = 1 / (µn Cox (W/L)(VGS − VT))

It replaces Rs with a voltage-controlled resistor.

---

## DC Results

<img width="1908" height="838" alt="dcsweep2" src="https://github.com/user-attachments/assets/cd274d12-d357-42f3-9c81-8347b3d4d79c" />


ID ≈ 3.8 µA  

Power:

P ≈ 1.8 × 3.8µA  
P ≈ 6.8 µW  

✔ Within limit

Vout ≈ 0.9 – 1.0 V

---

## Transient

<img width="1918" height="848" alt="TA2" src="https://github.com/user-attachments/assets/43745fde-784b-4782-aaf6-4ead5d854b29" />


```
SIN(0.75 10m 1k)
```

Observations:

- Inverted output
- Gain lower than resistive degeneration
- Good symmetry

---

## AC Analysis

<img width="1917" height="849" alt="AC2" src="https://github.com/user-attachments/assets/93adbabd-1b93-4287-b4fc-0c8ca063b8a7" />


Midband Gain ≈ 14–16 dB  

Linear Gain:

Av ≈ 5 – 6  

Bandwidth higher than Rs case.

---

## Inference

- MOS degeneration reduces gain.
- Increases bandwidth.
- CMOS-compatible solution.
- Bias dependent resistance.

---

# Gate-Tied MOS Degenerated CS (Self Bias)

---

## Circuit Diagram


<img width="1112" height="728" alt="cktdgm3" src="https://github.com/user-attachments/assets/32b1dfe8-bc3f-460b-8d1e-c3bcbff795f7" />




---

## Description

- Gate of M3 connected to Vi.
- No separate VBN.
- Strong local negative feedback.

---

## DC Behavior

<img width="848" height="632" alt="dcop3" src="https://github.com/user-attachments/assets/80e7e54d-92b6-4867-a4c7-2e4ccccb216d" />


For Vi ≈ 1.21V:

Vout ≈ 0.87 V  

ID ≈ 3 – 4 µA  


<img width="1918" height="847" alt="dcsweep3" src="https://github.com/user-attachments/assets/78049f89-22ba-4f69-9833-64320a6f6894" />


Power:

P ≈ 6 – 7 µW  

✔ Within limit

---

## Transient

```
SIN(1.21 10m 1k)
```

<img width="1918" height="848" alt="TA3" src="https://github.com/user-attachments/assets/805b6958-4b9e-49bf-a4f5-99aa3587e683" />


Observations:

- Lowest gain
- Highest linearity
- Strong feedback behavior

---

## AC Results

<img width="1918" height="847" alt="AC3" src="https://github.com/user-attachments/assets/82821c85-78b4-4ee0-99de-1423cf2e92fe" />


Midband Gain ≈ 10–12 dB  

Linear Gain:

Av ≈ 3 – 4  

Highest bandwidth among three.

---

# Comparison of All Three Designs

| Parameter | Rs Degeneration | MOS (Fixed VBN) | Gate-Tied MOS |
|------------|----------------|----------------|---------------|
| ID | ~3.5 µA | ~3.8 µA | ~3–4 µA |
| Power | ~6.3 µW | ~6.8 µW | ~6–7 µW |
| Gain (dB) | 18–20 dB | 14–16 dB | 10–12 dB |
| Linear Gain | 8–10 | 5–6 | 3–4 |
| Bandwidth | Moderate | Higher | Highest |
| Linearity | Good | Better | Best |
| Stability | Good | Better | Excellent |
| CMOS Integration | No | Yes | Yes |

---

# Overall Observations

1. Source degeneration reduces gain.
2. Degeneration improves linearity.
3. MOS-based degeneration improves integration.
4. Gate-tied configuration introduces strongest feedback.
5. Gain–Bandwidth tradeoff clearly verified.
6. All designs satisfy power < 20 µW.

---

# Conclusion

Three source-degenerated CS amplifier configurations were designed and simulated in 180nm CMOS.

The study verifies:

- Effect of source degeneration
- Gain–bandwidth tradeoff
- Feedback impact on amplifier behavior
- CMOS implementation advantages

The simulated results match theoretical small-signal analysis.

---

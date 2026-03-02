# Experiment 1: Resistive Load CS Amplifier

**Simulation Tool:** LTspice  
**Technology:** TSMC 180nm CMOS 

---

## Aim


To design and simulate a Resistive Load Common-Source (CS) Amplifier using 180nm CMOS technology.


## Components Used

| Component | Value / Model |
|-----------|--------------|
| NMOS | W = 540nm , L = 180nm |
| R | 20kΩ, 75kΩ, 90kΩ, 130kΩ |
| Supply Voltage | 1.8 V |
| Load Capacitor | 1 pF |
| Input Source | Sinusoidal |
| DC Offset | 0.549 V |
| AC Amplitude | 1 V (for AC analysis) |



## Design Details

- Channel Length (L) fixed at 180nm (technology minimum)
- Channel Width (W) initially 540nm (W/L = 3)
- Load capacitor of 1pF connected at output node duing AC analysis 
- R varied to study gain variation
- Q-point selected using DC sweep


## Procedure


### Step 1: Circuit Setup
1. Draw NMOS transistor (180nm technology model).
2. Set:
   - L = 180nm
   - W = 540nm (initial)
3. Connect R between drain and VDD (1.8 V).
4. Ground the source terminal.
5. Apply DC voltage source at gate.


# A)Circuit Diagram


<img width="1268" height="821" alt="image" src="https://github.com/user-attachments/assets/34596f12-c655-4017-8b0b-778fea5716c7" />



# B) DC Analysis and Calculations 

### Objective:
To determine operating region and select optimal bias point.


## a) DC Operating Point


## Procedure


### Step 2: Perform DC Operating Point Analysis
1. Go to:
   Simulate → Edit Configure Analysis → Operating Point
2. Place the .op command on schematic.
3. Run simulation.
4. Note:
   - ID
   - VDS
   - VGS
5. Verify MOSFET operates in saturation region.


<img width="846" height="635" alt="DC OP PNT" src="https://github.com/user-attachments/assets/93cc18c4-8835-47e7-9720-1286c376e282" />


## b) DC Sweep

### Step 3: Perform DC Sweep Analysis
1. Go to:
   Simulate → Edit Configure Analysis → DC Sweep
2. Select:
   - Sweep Variable: Voltage source (Vin)
   - Start: 0 V
   - Stop: 1.8 V
   - Step: 0.01 V
3. Run simulation.
4. Plot V(out) vs Vin.
5. Identify:
   - Steepest curve (for different RD values).
6. Choose midpoint:
   Vout ≈ VDD/2 = 0.9 V
7. Note corresponding Vin → DC Offset (0.549 V).


<img width="1918" height="850" alt="dcsweep90k" src="https://github.com/user-attachments/assets/c2b135ba-ed13-469d-a492-07361e70dc23" />


### 1. Drain Current

From DC operating point:

ID = 6.84951 × 10⁻⁶ A  
ID = 6.85 µA  

---

### 2. Output Voltage Calculation

Formula:

Vout = VDD − (ID × RD)

Substituting values:

Vout = 1.8 − (6.85 × 10⁻⁶ × 130000)

Vout = 1.8 − 0.8905  

Vout ≈ 0.91 V  

This confirms the midpoint condition (≈ 0.9 V).

---

### 3. Saturation Condition Check

Condition for saturation:

VDS > (VGS − VT)

Assuming:

VT ≈ 0.45 V  
VGS = 0.549 V  

VGS − VT = 0.099 V  

Since:

VDS ≈ 0.9 V >> 0.099 V  

The MOSFET operates in saturation region.

---


# Effect of Varying R

- Increasing R increases gain.
- Increasing R reduces bandwidth.
- Demonstrates gain–bandwidth tradeoff.
  

<img width="1918" height="850" alt="dcsweepvarR" src="https://github.com/user-attachments/assets/19981c97-ca8f-4314-8324-f06d2bae609b" />



# Effect of Varying W

- Increasing W increases drain current.
- gm increases.
- Gain increases.
- Q-point shifts left in transfer curve.

<img width="1918" height="847" alt="dcsweepvarW" src="https://github.com/user-attachments/assets/da82d59c-a5eb-44d5-93bb-1497dde596a0" />


### Observations:

- Increasing R increases voltage gain.
- Steepest transfer characteristic observed for R = 130kΩ.
- Midpoint condition:

    Vout = VDD / 2 = 0.9 V

- Corresponding input bias voltage:

    Vin = 0.549 V


### Inference:

- MOSFET operates in saturation region at selected Q-point.



# C) Transient Analysis and  Calculations


### Input Applied :

SIN(0.549 10m 1k)

- DC offset = 0.549 V
- Amplitude = 10 mV
- Frequency = 1 kHz

  
## Procedure 

### Step 4: Modify Input Source
Set input as:

SIN(0.549 10m 1k)

Where:
- 0.549 = DC offset
- 10m = amplitude
- 1k = frequency



### Step 5: Add Transient Command
1. Go to:
   Simulate → Edit Configure Analysis → Transient
2. Set stop time (e.g., 5ms).
3. Place .tran command.
   


### Step 6: Run Simulation
1. Click on output node (V(out)).
2. Click on input node (V(in)).
3. Split pane if required:
   Plot Settings → Add Plot Pane
   


### Step 7: Observe
1. Confirm:
   - Output is inverted (180° phase shift).
   - No clipping.
2. Measure amplitude.
3. Calculate gain = Vout/Vin.


<img width="1918" height="847" alt="transient analysis" src="https://github.com/user-attachments/assets/629a7607-7053-4e9e-a9d5-981fe7ba9a09" />


### 1. Input Signal

Vin = 0.549 + 10mV sin(2πft)  

Where:

f = 1 kHz  

---

### 2. Gain Conversion (from AC result)

Midband Gain ≈ 30 dB  

Linear gain:

Av = 10^(30/20)

Av ≈ 31.6  

---

### 3. Output Amplitude

Input amplitude = 10 mV  

Output amplitude:

Vout = 31.6 × 10 mV  

Vout ≈ 316 mV  

Output swings around:

0.9 V ± 0.316 V  

Range:

0.584 V to 1.216 V  

No clipping observed.



### Observations:

- Output waveform is inverted (180° phase shift).
- Output DC level ≈ 0.9 V.


### Inference:

- CS amplifier shows proper amplification.
- Amplifier operates in active region.



# D) AC Analysis and  Calculations

### AC Command Used :

.ac dec 100 1 1G

## Procedure 

### Step 8: Modify Input Source
1. Keep DC value = 0.549 V.
2. Set AC amplitude = 1.



### Step 9: Add AC Command
1. Go to:
   Simulate → Edit Simulation Cmd → AC Analysis
2. Select:
   - Type: Decade
   - Points/decade: 100
   - Start: 1 Hz
   - Stop: 1 GHz
3. Place .ac command.



### Step 10: Run Simulation
1. Click output node.
2. Plot:
   dB(V(out)) for gain.
3. Observe:
   - Midband gain
   - -3 dB cutoff frequency
   - Phase response



<img width="1916" height="850" alt="image" src="https://github.com/user-attachments/assets/1c06dc4f-a527-41ee-b125-6a9f7de44b35" />



### 1. Transconductance (gm)

Formula:

gm = 2ID / (VGS − VT)

gm = (2 × 6.85 µA) / 0.099  

gm ≈ 0.000138 A/V  

gm ≈ 0.138 mS  

---

### 2. Theoretical Voltage Gain

Av = −gm × RD  

Av = −(0.000138 × 130000)

Av ≈ −17.9  

(Theoretical value slightly differs due to model parameters and parasitic effects.)

---

### 3. High Frequency Cutoff

Output load capacitor CL = 1 pF  

Formula:

fH = 1 / (2πRC)

fH = 1 / (2π × 130k × 1pF)

fH ≈ 1.22 MHz  

This matches the simulated cutoff frequency (~1 MHz).

---

### 4. Bandwidth

Since no coupling capacitors are used:

Bandwidth ≈ fH  

Bandwidth ≈ 1 MHz  

---


### Observations:

- High-frequency cutoff ≈ 1 MHz
- Phase shift confirms inverting behavior.


---

# Overall Inferences

1. Proper biasing is essential for symmetrical output swing.
2. Gain is directly proportional to R.
3. Bandwidth is inversely proportional to R.
4. Output capacitor introduces dominant pole.
5. CS amplifier exhibits 180° phase inversion.
6. Gain–bandwidth tradeoff observed experimentally.

---

# Conclusion

-The Resistive Load CS Amplifier was successfully designed and simulated using 180nm CMOS technology in LTspice.
-The effect of varying load resistance (RD), transistor width (W), and bias voltage was studied through DC, Transient, and AC analysis. 
-The experiment clearly verifies the gain–bandwidth tradeoff and the inverting nature of the Common Source amplifier.

---



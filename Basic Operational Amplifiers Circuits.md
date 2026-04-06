# BASIC OPERATIONAL AMPLIFIER CIRCUITS

## Aim

To design and analyze various operational amplifier circuits:

1. Zero Crossing Detector (ZCD)
 - Inverting ZCD
 - Non - Inverting ZCD
2. Comparator  
 - Inverting Comparator
 - Non-Inverting Comparator 
3. Inverting Amplifier  
4. Non-Inverting Amplifier  
5. Voltage Follower  



## Components Used

| Component | Specification |
|----------|--------------|
| Op-Amp | uA741 |
| Resistors | 1kΩ, 500Ω (typical) |
| Power Supply | ±15 V |
| Input Signal | Sinusoidal |
| Simulation Tool |Tina-TI |



## Theory



# A) Zero Crossing Detector (ZCD)

A Zero Crossing Detector compares the input signal with **0V reference**.

- If input > 0 → Output = +Vsat  
- If input < 0 → Output = −Vsat  



## Types of ZCD

# 1. Inverting Zero Crossing Detector

## Circuit Description
- Input is applied to **inverting terminal (−)**
- Non-inverting terminal is grounded (0V)


## Circuit Diagram 


<img width="1272" height="753" alt="inverting zcd ckt" src="https://github.com/user-attachments/assets/9130bb74-f10f-4906-873e-98e2167e0d47" />


## Operation


## Input

Vin = 5 sin(2000 pi t)




| Condition | Output |
|----------|--------|
| Vin > 0 | −13 V |
| Vin < 0 | +13 V |


## Output Waveform 


<img width="1918" height="876" alt="inverting zcd graph" src="https://github.com/user-attachments/assets/a7ceb40f-a635-49ea-93f6-18454469df33" />



## Observation
- Output is inverted square wave
- 180° phase shift from input



# 2. Non-Inverting Zero Crossing Detector

## Circuit Description
- Input is applied to **non-inverting terminal (+)**
- Inverting terminal is grounded (0V)


## Circuit Diagram 


<img width="1026" height="658" alt="non inverting ZCD ckt" src="https://github.com/user-attachments/assets/14cd5d11-0fe4-4274-932f-a4eef07ac89b" />



## Operation


## Input

Vin = 5 sin(2000 pi t)

| Condition | Output |
|----------|--------|
| Vin > 0 | +13 V |
| Vin < 0 | −13 V |

## Output Waveform 



<img width="1918" height="872" alt="non inverting ZCD graph " src="https://github.com/user-attachments/assets/e74ba22e-053d-477b-8822-92d815da8aef" />




## Observation
- Output is in phase with input
- Clean square wave generation



## Inference

- ZCD converts analog sine wave into digital signal  
- Useful in frequency measurement and waveform shaping  



# B) Comparator



## Principle

A comparator compares input voltage with a **reference voltage (Vref ≠ 0)**.


## Types of Comparator

# 1. Inverting Comparator

## Circuit Description
- Input applied to **inverting terminal (−)**
- Reference voltage applied to **non-inverting terminal (+)**

## Circuit Diagram 

<img width="1175" height="727" alt="inverting comparator op amp ckt" src="https://github.com/user-attachments/assets/bcb6c257-9c7b-4b6b-8df5-1c5255acdb5e" />


## Operation

| Condition | Output |
|----------|--------|
| Vin > Vref | −13 V |
| Vin < Vref | +13 V |

## Output Waveform 

<img width="1918" height="875" alt="inverting comparator graph" src="https://github.com/user-attachments/assets/dff3a46f-d898-4c67-bd57-cd368b3c00f4" />


## Observation
- Output is inverted with respect to input
- Switching occurs at Vref

---

# 2. Non-Inverting Comparator

## Circuit Description
- Input applied to **non-inverting terminal (+)**
- Reference voltage applied to **inverting terminal (−)**


## Circuit Diagram 

<img width="1152" height="718" alt="non inverting comparator ckt" src="https://github.com/user-attachments/assets/1a1b508f-4aee-4aee-b5bc-b7fa26091398" />


## Operation

| Condition | Output |
|----------|--------|
| Vin > Vref | +13 V |
| Vin < Vref | −13 V |

## Output Waveform 


<img width="1916" height="882" alt="non inverting comparator graph " src="https://github.com/user-attachments/assets/6fcfef52-8eb5-4717-b82f-8a95bc9cb082" />



## Observation
- Output follows input polarity
- Used for level detection

---

## Inference

- Comparator acts as a **level detector**
- Threshold shifts waveform switching point  

---

# C) Inverting Amplifier

## Circuit Description 

- Input applied to **inverting terminal**
- Non-inverting terminal grounded

## Circuit Diagram 


<img width="963" height="667" alt="inverting ckt" src="https://github.com/user-attachments/assets/c58ad6d5-7251-4dd4-818a-8b8f64422b7e" />


---

## Gain Formula


Av = Vout/Vin = -R_f/R_1


---

## Output Waveform


<img width="1918" height="863" alt="inverting graph" src="https://github.com/user-attachments/assets/e4f9fd27-7af2-4590-a0fe-9c634c3eecd1" />



## Observations

- Output is **180° out of phase**
- Gain depends on resistor ratio  

---

## Inference

- Provides signal inversion  
- Widely used in signal processing  

---

# D) Non-Inverting Amplifier

## Circuit Description

- Input applied to **non-inverting terminal**
- Feedback network used  


## Circuit Diagram 


<img width="1041" height="695" alt="non inverting ckt" src="https://github.com/user-attachments/assets/d50e9f91-5fec-497a-a327-b6f34f07728c" />


---

## Gain Formula


A_v = 1 + (R_f/R_1)



## Output Waveform


<img width="1916" height="866" alt="non inverting graph" src="https://github.com/user-attachments/assets/7cb5624a-3ca7-4587-b735-da1144e2744d" />


---

## Observations

- Output is **in phase** with input  
- Gain is always **≥ 1**  

---

## Inference

- Used where signal amplification without inversion is required  

---

# E) Voltage Follower (Buffer)

## Circuit Diagram 

<img width="856" height="658" alt="Voltage follower ckt " src="https://github.com/user-attachments/assets/74bbe24c-1d5b-456c-bebf-cc75648ff55b" />


## Output Waveform

<img width="1918" height="853" alt="Voltage follower graph " src="https://github.com/user-attachments/assets/71067e44-9102-47bf-962b-8ffabacdfc1e" />

## Principle

- Special case of non-inverting amplifier  
- Gain = 1  

Av = 1

---

## Observations

- Output follows input exactly  
- No phase shift  

---

## Inference

- Used for **impedance matching**
- Prevents loading effect  

---

# Simulation Details

## Input Signal


Vin = 5 sin(2000 pi t)


- Frequency = 1 kHz  
- Amplitude = 5 V  

---

## Supply Voltages

-  V_{CC} = +15V   
-  V_{EE} = -15V  

---

## Practical Observation

- Output saturation observed at: 13 V

---

## Reason

- uA741 is **not rail-to-rail**
- Internal voltage drops limit output swing  

---

## Results

## 1. ZCD Output
- Square wave   

## 2. Comparator Output
- Asymmetric square wave  
 
## 3. Inverting Amplifier
- Output inverted  

## 4. Non-Inverting Amplifier
- Output in phase  

### 5. Voltage Follower
- Output = Input  

---

## Observations Table

| Circuit | Key Feature | Output |
|--------|------------|--------|
| ZCD | Zero reference | Square wave |
| Comparator | Threshold detection | Shifted square wave |
| Inverting Amp | Phase inversion | Amplified inverted signal |
| Non-Inverting Amp | No inversion | Amplified signal |
| Voltage Follower | Unity gain | Same as input |

---

## Overall Inferences

1. Op-amp works as comparator in open-loop mode  
2. ZCD detects zero crossings accurately  
3. Comparator shifts switching threshold  
4. Amplifiers provide controlled gain  
5. uA741 shows non-ideal behavior (±13V saturation)  
6. Slew rate affects output transitions  

---

## Conclusion

The experiment successfully demonstrated the operation of various op-amp configurations using the uA741 IC.

- Zero Crossing Detector and Comparator verified switching behavior  
- Inverting and Non-Inverting amplifiers demonstrated gain and phase properties  
- Voltage follower confirmed unity gain buffering  

The results align with theoretical expectations and highlight practical limitations such as **non-rail-to-rail output and slew rate effects**.

---
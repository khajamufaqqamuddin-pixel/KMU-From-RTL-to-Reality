# Day-2
<h1 align="center">🧠 CMOS Circuit Design – Theory & Conceptual Background</h1>

<p align="center">
  <b>(Based on Sky130 PDK and SPICE Simulation Methodology)</b><br>
  Week-4 Task – CMOS Design and Device Characterization
</p>

---

## 1️⃣ MOSFET Behavior & Id–Vds Characteristics

### 🎯 Objective
Analyze the drain current (𝐼<sub>D</sub>) as a function of the drain-to-source voltage (𝑉<sub>DS</sub>) for different gate voltages (𝑉<sub>GS</sub>), identifying **linear** and **saturation** regions.

### 🧩 Theory
The drain current of an NMOS transistor:

### NMOS Drain Current Equation

The drain current \( I_D \) of an NMOS transistor is given by:

![ID equation](https://latex.codecogs.com/svg.image?I_D%20=%20%5Cbegin%7Bcases%7D%200%2C%26%20V_%7BGS%7D%20%3C%20V_%7BTH%7D%20%5C%5C%20%5Cmu_n%20C_%7Box%7D%20%5Cfrac%7BW%7D%7BL%7D%5B(V_%7BGS%7D-V_%7BTH%7D)V_%7BDS%7D-%5Cfrac%7BV_%7BDS%7D%5E2%7D%7B2%7D%5D%2C%26%20V_%7BDS%7D%20%3C%20(V_%7BGS%7D-V_%7BTH%7D)%5C%20%5Ctext%7B(Linear)%7D%20%5C%5C%20%5Cfrac%7B1%7D%7B2%7D%5Cmu_n%20C_%7Box%7D%20%5Cfrac%7BW%7D%7BL%7D(V_%7BGS%7D-V_%7BTH%7D)%5E2(1%2B%5Clambda%20V_%7BDS%7D)%2C%26%20V_%7BDS%7D%20%5Cge%20(V_%7BGS%7D-V_%7BTH%7D)%5C%20%5Ctext%7B(Saturation)%7D%20%5Cend%7Bcases%7D)



Where:  
- 𝜇ₙ → Electron mobility  
- 𝐶ₒₓ → Oxide capacitance per unit area  
- 𝑉ₜₕ → Threshold voltage  
- λ → Channel-length modulation parameter  

### 📊 Observation
- For low 𝑉<sub>DS</sub>: 𝐼<sub>D</sub> increases linearly → **Ohmic region**.  
- For 𝑉<sub>DS</sub> > (𝑉<sub>GS</sub> − 𝑉<sub>TH</sub>): 𝐼<sub>D</sub> saturates → **Active region**.  
- Short-channel devices exhibit **velocity saturation**, where 𝐼<sub>D</sub> stops increasing with higher 𝑉<sub>DS</sub>.

---

## 2️⃣ Threshold Voltage Extraction & Velocity Saturation

### 🎯 Objective
Determine the **threshold voltage (Vₜ)** of the MOSFET and observe **velocity saturation**.

### 🧩 Theory
From the Id–Vgs curve (fixed Vds):

![ID equation](https://latex.codecogs.com/svg.image?I_D%20=%20K(V_%7BGS%7D%20-%20V_T)%5E2%20%5Cquad%20%5Ctext%7Bwhere%7D%5Cquad%20K%20=%20%5Cfrac%7B1%7D%7B2%7D%5Cmu_n%20C_%7Box%7D%20%5Cfrac%7BW%7D%7BL%7D)

- Plotting √I<sub>D</sub> vs V<sub>GS</sub> → **x-intercept = V<sub>T</sub>**

### ⚡ Velocity Saturation
At smaller L and high fields:

![ID velocity saturation](https://latex.codecogs.com/svg.image?I_D%20=%20W%20C_%7Box%7D%20v_%7Bsat%7D%20(V_%7BGS%7D%20-%20V_T))

- Current becomes **linear** in (V<sub>GS</sub> − V<sub>T</sub>)  
- Dominant in deep submicron devices

---

## 3️⃣ CMOS Inverter – Voltage Transfer Characteristic (VTC)

### 🎯 Objective
Analyze **VTC (Vout vs Vin)** for a CMOS inverter.

### ⚙️ Theory
A CMOS inverter = PMOS (pull-up) + NMOS (pull-down)

| Vin | PMOS | NMOS | Vout |
|-----|-------|-------|------|
| Low | ON | OFF | ≈ VDD |
| High | OFF | ON | ≈ 0 |
| Mid | Partially ON | Partially ON | Switching region |

Switching threshold 𝑉<sub>M</sub> occurs when I<sub>NMOS</sub> = I<sub>PMOS</sub>.

![VM switching threshold](https://latex.codecogs.com/svg.image?V_M%20%E2%89%88%20%5Cfrac%7BV_%7BDD%7D%20%2B%20%7CV_%7Btp%7D%7C%20%2B%20(%5Cmu_n%20%2F%20%5Cmu_p)V_%7Btn%7D%7D%7B1%20%2B%20(%5Cmu_n%20%2F%20%5Cmu_p)%7D)


### 📈 VTC Plot
Shows three regions:
- High output (VOH)
- Transition (Switching)
- Low output (VOL)

---

## 4️⃣ Transient Behavior – Rise/Fall Delay Analysis

### 🎯 Objective
Study the **propagation delay** of a CMOS inverter using pulse input.

### 🧩 Theory
When input changes:

- **t<sub>pLH</sub>** → Output rises from 50% low → 50% high  
- **t<sub>pHL</sub>** → Output falls from 50% high → 50% low  
- **Average delay:**

![Propagation Delay](https://latex.codecogs.com/svg.image?t_p%20%3D%20%5Cfrac%7Bt_%7BpHL%7D%20%2B%20t_%7BpLH%7D%7D%7B2%7D)


### 🔍 Dependence
- ↑ Width (W) → ↓ Resistance → ↓ Delay  
- ↑ Load Capacitance (C<sub>L</sub>) → ↑ Delay  
![Delay Equation](https://latex.codecogs.com/svg.image?t_{delay}%20%5Cpropto%20R_{on}%20%5Ctimes%20C_L)


### 📘 STA Relevance
These measured delays correspond to **cell timing arcs** in **Static Timing Analysis (STA)**.

---

## 5️⃣ Noise Margin & Robustness Analysis

### 🎯 Objective
Quantify **noise tolerance** from the VTC.

### ⚙️ Theory
From the VTC:

- V<sub>OH</sub> ≈ VDD  
- V<sub>OL</sub> ≈ 0V  
- V<sub>IH</sub>, V<sub>IL</sub> → points where dVout/dVin = −1  

![Noise Margins](https://latex.codecogs.com/svg.image?NM_H%20%3D%20V_{OH}%20-%20V_{IH},%20%5Cquad%20NM_L%20%3D%20V_{IL}%20-%20V_{OL})


### 📊 Interpretation
- High noise margin → stronger logic robustness  
- Reduced NMH/NML → sensitive to small voltage variations

---

## 6️⃣ Power Supply & Device Variation Studies

### 🎯 Objective
Study the impact of **VDD** and **W/L sizing** on inverter performance.

### ⚙️ Theory
**VDD Variation**
- ↑ VDD → Higher (VGS−Vt) → Faster switching, smaller delay  
- ↓ VDD → Lower drive, degraded noise margin  

**Device Sizing**
- ↑ PMOS width → Vm ↓  
- ↑ NMOS width → Vm ↑  
- Affects rise/fall symmetry and noise margins  

### 📘 STA Link
VDD, temperature, and device variations form **PVT corners** in STA timing analysis.

---

## 🧾 Summary Table of Key Parameters

| Parameter | Meaning | Extraction Method | Typical Use |
|------------|----------|------------------|--------------|
| Vth | Threshold voltage | From Id–Vgs extrapolation | Device characterization |
| Vm | Switching threshold | Point where Vin = Vout (VTC) | Logic reference |
| tpHL / tpLH | Propagation delays | Transient at VDD/2 crossings | Timing analysis |
| NMH / NML | Noise margins | From VTC slopes | Noise immunity |
| Id_sat | Saturation current | From Id–Vds curve | Drive strength |

---

## 7️⃣ Conceptual Link to Static Timing Analysis (STA)

| Physical Parameter | STA Equivalent | Explanation |
|--------------------|----------------|--------------|
| Channel resistance, mobility | Cell delay models | Defines delay under load |
| Vth variation | SS/TT/FF corners | Causes delay shifts |
| VDD variation | Voltage corners | Impacts setup/hold slack |
| Temperature, process variation | PVT corners | Bounds timing |
| Noise margin | Logic robustness | Ensures correct switching |

---

## 🧩 Conclusion
This CMOS circuit design module bridges **device physics** and **timing analysis**.

Through SPICE simulations, you observe how transistor-level effects directly determine:
- Delay & power trade-offs  
- Switching thresholds  
- Noise tolerance  
- STA timing margins under variation  

Understanding these relationships builds a strong foundation for **VLSI timing analysis** and **STA-driven design closure**.

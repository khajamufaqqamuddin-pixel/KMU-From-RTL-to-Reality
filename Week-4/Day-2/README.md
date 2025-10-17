# DAY-1
This repository demonstrates SPICE-based NMOS transistor analysis — from theoretical understanding to simulation using Ngspice.

## 📗 Topics Covered
1. Why SPICE simulations are needed  
2. NMOS transistor basics  
3. Threshold voltage and substrate bias  
4. Resistive (Linear) region operation  
5. Saturation (Active) region operation  
6. Drift current theory  
7. Drain current models  
8. SPICE setup and syntax  
9. Technology parameters  

## 🧠 Why SPICE Simulations?
SPICE (Simulation Program with Integrated Circuit Emphasis) is essential for:
- Predicting circuit behavior before fabrication  
- Performing DC, AC, and transient analysis  
- Verifying transistor models  
- Bridging mathematical theory and real-world circuits  

# Introduction to SPICE Simulations

SPICE is a circuit simulator that models electronic components mathematically. It is used to verify circuit performance before physical implementation.

### Why We Need SPICE:
- To simulate and predict circuit behavior
- To perform DC, AC, and transient analyses
- To identify design errors early
- To understand transistor operation regions

SPICE saves cost and time in chip design and testing.
# NMOS Basics

The NMOS transistor has four terminals:
- Gate (G)
- Drain (D)
- Source (S)
- Body/Substrate (B)

### Operation Regions:
1. Cutoff: Vgs < Vth → No current
2. Linear/Resistive: Vds < (Vgs - Vth)
3. Saturation: Vds ≥ (Vgs - Vth)

NMOS works as a voltage-controlled current source.
# Threshold Voltage

The threshold voltage (Vth) is the minimum gate-to-source voltage required to create a conductive channel.

### Formula:
Vth = VTO + γ ( √(2ΦF + VSB) - √(2ΦF) )

Where:
- VTO → zero-bias threshold voltage  
- γ → body-effect coefficient  
- ΦF → surface potential  
- VSB → substrate bias voltage  

A positive substrate potential increases Vth.
# Resistive (Linear) Region

Condition: Vds < (Vgs - Vth)

### Drain Current:
ID = K [ (Vgs - Vth) * Vds - (Vds² / 2) ]

This region behaves like a voltage-controlled resistor.

SPICE can be used to simulate the I–V characteristics under small Vds values.
# Saturation (Active) Region

Condition: Vds ≥ (Vgs - Vth)

### Drain Current:
ID = (1/2) K (Vgs - Vth)² (1 + λVds)

Here, channel pinches off near the drain. The current becomes nearly constant, controlled by Vgs.

This region is used in amplifier circuits.
# SPICE Setup

1. Install Ngspice: `sudo apt install ngspice`
2. Create a `.cir` file with circuit description
3. Include transistor model using `.include`
4. Run simulation: `ngspice filename.cir`
5. Use `.plot`, `.dc`, or `.tran` for plotting
# SPICE Syntax Basics

| Command | Description |
|----------|--------------|
| V | Voltage source |
| I | Current source |
| R | Resistor |
| M | MOSFET |
| .dc | DC sweep |
| .tran | Transient analysis |
| .ac | Frequency analysis |
| .plot | Plot output |
| .model | Define transistor model |

Example:
```
M1 drain gate source body model_name L=1u W=10u
```
# Technology Parameters

| Parameter | Description | Typical Value |
|------------|--------------|----------------|
| VTO | Threshold voltage | 0.7 V |
| KP | Transconductance parameter | 50 µA/V² |
| LAMBDA | Channel length modulation | 0.02 |
| PHI | Surface potential | 0.6 V |
| GAMMA | Body effect coefficient | 0.4 |

# Week 2 – BabySoC Fundamentals & Functional Modelling

## 🎯 Objective
To build a solid understanding of SoC fundamentals and practice functional modelling of the BabySoC using simulation tools (**Icarus Verilog** & **GTKWave**).

---

## ✅ Task Checklist
- [x] Go through **Fundamentals of SoC Design** notes.  
- [x] Understand **What is a System-on-Chip (SoC)?**  
- [x] Learn the **Components of a typical SoC** (CPU, memory, peripherals, interconnect).  
- [x] Explore why **BabySoC is a simplified learning model**.  
- [x] Study the **role of functional modelling** before RTL & physical design.  
- [x] Write and upload **1–2 page summary on GitHub**.  

---


## BabySoc Block

🖼️
![BabySoC_block](https://github.com/khajamufaqqamuddin-pixel/KMU-From-RTL-to-Reality/blob/main/Week-2/BabySoC_block.png)



## 📘 1. What is a System-on-Chip (SoC)?
A **System-on-Chip (SoC)** is an integrated circuit that combines the essential building blocks of a computer system into a single chip.  
Instead of using separate chips for CPU, memory, and peripherals, an SoC integrates them to achieve:
- ⚡ High performance  
- 🔋 Power efficiency  
- 📏 Compact size  

SoCs are widely used in **smartphones, IoT devices, automotive systems, and embedded platforms**.

---

## 🧩 2. Components of a Typical SoC
A typical SoC consists of the following components:

- 🖥 **CPU (Processor):** Executes instructions and controls the system.  
- 💾 **Memory (RAM/ROM/Cache):** Stores data and instructions.  
- 🔌 **Peripherals:** Interfaces such as GPIO, UART, SPI, I²C, Timers, and ADC/DAC.  
- 🔗 **Interconnect (Bus/Fabric):** Provides communication between CPU, memory, and peripherals (e.g., AMBA AHB/AXI/APB).  

Together, these make the SoC function as a **complete standalone system**.

---

## 🍼 3. Why BabySoC?
**BabySoC** is a simplified learning model of an SoC designed for students and beginners:  

- 📚 Helps in **understanding SoC concepts** without overwhelming complexity.  
- 🛠 Provides hands-on practice using open-source tools like **Icarus Verilog** and **GTKWave**.  
- 🔍 Focuses on **CPU-memory-peripheral interactions**.  
- 🎓 Acts as a **stepping stone** toward more advanced SoC design (RTL → Physical Design).  

---

## 🛠 4. Role of Functional Modelling
Functional modelling is the **first step** before RTL design and physical implementation:  

- ✅ Ensures correct **system-level behavior**.  
- 🧪 Verifies **CPU ↔ Memory ↔ Peripheral communication**.  
- 🐞 Detects **logical errors early**, saving time in later design stages.  
- 🔄 Provides a **simulation-driven learning approach**.  

Thus, functional modelling is like a **blueprint** that validates the design before moving to lower abstraction levels.

---

## 📌 5. Conclusion
BabySoC is a simplified but powerful platform that introduces the **fundamentals of SoC design**.  
By working with BabySoC and performing **functional modelling**, learners can understand how different components interact, gain debugging experience, and build confidence for transitioning into **RTL design, synthesis, and physical design**.

---


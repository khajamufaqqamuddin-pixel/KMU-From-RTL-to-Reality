# ⚙️ Week 5 Task – OpenROAD Flow Setup and Floorplan + Placement

<p align="center">
  <img src="https://img.shields.io/badge/OpenROAD-Flow-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/Stage-Floorplan%20%26%20Placement-green?style=flat-square" />
  <img src="https://img.shields.io/badge/Week-5-orange?style=flat-square" />
  <img src="https://img.shields.io/badge/Author-KMU-lightgrey?style=flat-square" />
</p>

<p align="center">
  🧩 <b>VLSI Physical Design Flow using OpenROAD</b><br>
  From SPICE-level simulation to layout implementation
</p>

---

## 🧠 Objective
Set up **OpenROAD Flow Scripts** and execute **only the Floorplan and Placement stages** of the physical design flow.
This step transitions from transistor-level SPICE design (Week 4) to backend implementation, converting logic into a physical layout.

---

## 🏗️ Step 1: Install OpenROAD Flow Scripts

### 🔹 Clone Repository
```bash
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
```

### 🔹 Install Prerequisites (Reference)
Refer to: [spatha_vsd-hdp – Day14 README](https://github.com/spatha0011/spatha_vsd-hdp/blob/main/Day14/README.md)

Install dependencies:
```bash
sudo apt update
sudo apt install -y build-essential python3 python3-venv python3-tk git cmake gcc g++ make
```

### 🔹 Setup Environment
```bash
sudo ./setup.sh
```

### 🔹 Verify Installation
```bash
source ./env.sh
yosys -help  
openroad -help
```
Expected output:
```
Usage: flow.tcl -design <design> [-to <stage>] [-from <stage>] [-verbose]
Example: ./flow.tcl -design gcd -to placement
```
If this appears, OpenROAD Flow is successfully installed.

---

## 🧩 Step 2: Run Floorplan and Placement

### 🔹 Example Flow Execution
Run the flow up to placement using the included `gcd` design:
```bash
./flow.tcl -design gcd -to placement
```

### 🔹 Sample Terminal Log Snippets
**Floorplan Stage:**
```
[INFO] Running Floorplan...
[INFO] Core area defined: (10, 10) to (1500, 1500)
[INFO] Pin placement completed.
[INFO] Floorplan stage completed successfully.
```

**Placement Stage:**
```
[INFO] Global placement started.
[INFO] Legalization completed.
[INFO] Detailed placement finished.
[INFO] Placement stage completed successfully.
```

Logs and reports will be saved automatically in:
```
runs/<timestamp>/logs/
```

---

## 📸 Step 3: Capture Deliverables

### 1️⃣ **Screenshots / Proof**
- Terminal with executed commands
- Visible Linux username (e.g., `kmu@ubuntu:~$`)
- OpenROAD setup confirmation
- Floorplan & placement success logs






#### 🧩 Steps Followed
1. Installed prerequisites and cloned OpenROAD Flow Scripts.
2. Verified environment using `./flow.tcl -help`.
3. Executed flow up to placement using `./flow.tcl -design gcd -to placement`.
4. Captured floorplan and placement layouts.

#### ⚙️ Commands Used
```bash
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
cd OpenROAD-flow-scripts
./setup.sh
./flow.tcl -design gcd -to placement
```

####
| Stage | Description |  |
|--------|--------------|-------------|
| Installation | Successful OpenROAD setup and environment verification |  |
| Floorplan | Core/die generation and pin placement |  |
| Placement | Standard cells arranged successfully |  |
| Logs | Flow completion proof |  |

#### 🧠 Challenges Faced
- Encountered dependency issues (`gcc`, `cmake`, `python3-tk` missing).
- Resolved by manually installing packages using apt.
- Verified all stages executed successfully.

#### ✅ Outcome
- Installed OpenROAD Flow Scripts successfully.
- Completed Floorplan and Placement.
- Captured logs and layout views for documentation.

---

## 🚀 Next Steps (Week 6 Preview)
You’ll move from placement to **Clock Tree Synthesis (CTS)** and **Routing**, completing the physical design flow toward final GDSII generation.

---

## 🏁 Credits
**Author:** Khaja Mufaqqam Uddin  
**Institute:** VSD (Chips-to-Startup Program)  
**Flow:** OpenROAD Flow Scripts (Nangate45 PDK)  
**Mentor Reference:** [spatha_vsd-hdp Day14 Repo](https://github.com/spatha0011/spatha_vsd-hdp/blob/main/Day14/README.md)

<p align="center">
  💻 *Empowering Open-Source VLSI Education – Week 5 Physical Design Task Completed!* 💻
</p>

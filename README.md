# ⌨️ RISC-V SoC Tapeout Journey  

<div align="center">

![Static Badge](https://img.shields.io/badge/RISCV%20-%20SoC%20Tapeout-blue?style=for-the-badge)
![Static Badge](https://img.shields.io/badge/20%20-%20WEEKS-purple?style=for-the-badge)
![Static Badge](https://img.shields.io/badge/IIT_GANDHINAGAR%20-%20VSD%20-golden?style=for-the-badge)

</div>

---

## 🚀 About This Repository  
This is my **first GitHub repository** created as part of the **VSD SoC Tapeout Program (IIT Gandhinagar)**.  
Here, I document my **week-by-week progress** — from **RTL design to GDSII flow** in VLSI.  

The goal of this program (and this repo) is to:  
- Gain **hands-on experience** with RISC-V SoC design.  
- Learn the **end-to-end physical design flow** of an IC.  
- Contribute toward the vision of **Viksit Bharat** and the **Indian Semiconductor Mission**.  

---

## 📅 Week 0 — Setup & Tool Installation  

| Task | Description | Status |
|------|-------------|--------|
| **Task 0** | 🛠️ Installed essential tools: **Icarus Verilog (iverilog)**, **Yosys**, and **GTKWave** for simulation, synthesis, and waveform analysis. | ✅ Done |

---

## 📅 Week 1 — RTL Design & Synthesis Fundamentals  

| Day | Focus Area | Description | Status |
|-----|------------|-------------|--------|
| **Day 1** | Verilog RTL Design & Simulation | Learnt the basics of **Verilog RTL design**, simulated with **iverilog**, analyzed outputs on **GTKWave**, and synthesized using **Yosys**. | ✅ Done |
| **Day 2** | Timing Libraries & Coding Styles | Understood **timing libraries**, explored **hierarchical vs flat synthesis**, and studied different **flop coding styles** for efficient design. | ✅ Done |
| **Day 3** | Logic Design Practice | Designed and simulated logic circuits (MUX, D-Flip Flop etc.), synthesized them, and verified timing reports. Strengthened understanding of RTL → Netlist flow. | ✅ Done |

---

## 📅 Week 2 — BabySoC Fundamentals & Functional Modelling  

| Task | Description | Status |
|------|-------------|--------|
| **Part 1** | 🧩 **SoC Fundamentals & BabySoC Architecture** | Explored the concept of a **System-on-Chip**, its components (CPU, Memory, Peripherals, Interconnect), and how **BabySoC** demonstrates real-world integration using **RVMYTH (RISC-V core)**, **PLL**, and **DAC**. | ✅ Done |
| **Part 2** | ⚙️ **Pre-Synthesis Functional Simulation** | Cloned the **VSDBabySoC** repo, compiled Verilog modules with `iverilog`, generated `.vcd` waveforms, and verified correct operation of clock, reset, and dataflow using **GTKWave**. | ✅ Done |
| **Part 3** | 🧠 **Post-Synthesis Simulation & Validation** | Performed synthesis to obtain gate-level netlist, simulated using `make post_synth_sim`, and verified waveform consistency between RTL and GLS ensuring functional equivalence. | ✅ Done |

**Learning Outcome:**  
Week 2 solidified understanding of **functional modelling** and **simulation methodologies**.  
It showcased how the **BabySoC** serves as a bridge between theoretical SoC design and practical implementation — validating both **logic correctness** and **synthesis integrity** before moving toward layout and tapeout.

---

## 📅 Week 3 — Post Synthesis GLS & STA Fundamentals  

| Task | Description | Status |
|------|-------------|--------|
| **Part 1** | 🎲 **Post Synthesis of GLS** |Performed the synthesis of BabySoC and Compared GLS output with functional simulation output . | ✅ Done |
| **Part 2** | 🔩 **Fundamentals of STA** |Completed the STA Fundamental course through Udemy. | ✅ Done |
| **Part 3** | ⌚ **Generate Timing Graphs with OpenSTA** | Loaded synthesized netlist and constraints into OpenSTA and generated the timing graphs. | ✅ Done |

**Learning Outcome:**  
Week 3 solidified understanding of **STA** and **GLS** fundamentals.  
It showcased how the **OpenSTA** is installed and then, used it practically for synthesizing the netlist and getting the timing graphs, which shows the practical hands on experience.



## ✨ Closing Note  
This repository is a **living document** of my Tapeout journey.  
Each completed week adds another step toward mastering **open-source VLSI design**.  

> *“The best way to learn VLSI is by doing it — one step at a time.”*

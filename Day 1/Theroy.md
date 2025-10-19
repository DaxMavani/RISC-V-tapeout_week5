# Day 1
##  Basics of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)

### <ins>Introduction to Circuit Design & SPICE Simulations</ins>

**Why do we need SPICE Simulations?**  
SPICE (Simulation Program with Integrated Circuit Emphasis) is the backbone of analog and digital circuit design. It allows engineers to **verify circuit behavior before fabrication**, saving both time and resources.  
Through SPICE, we can observe the impact of transistor parameters, voltage variations, and temperature on circuit performance — helping in **device characterization**, **power analysis**, and **robust design optimization**.  

By accurately modeling electronic components, SPICE enables simulation of both **DC characteristics** (like Id–Vds curves) and **transient responses**, providing a near-real understanding of how a fabricated circuit would behave.

---

### ⚛ <ins>NMOS Device Fundamentals</ins>

An **n-Channel MOSFET (NMOS)** operates as a voltage-controlled current source. It forms the foundation for most CMOS-based VLSI systems, including RISC-V SoC architectures.

#### 🧠 NMOS Structure  
1. **Source & Drain:** Two n+ doped terminals allowing electron flow when the transistor is ON.  
2. **Gate:** The control terminal, typically poly-silicon, modulates channel formation.  
3. **Gate Oxide (SiO₂):** A thin insulating layer that controls electrostatic interaction between gate and channel.  
4. **Body (Substrate):** A p-type base connected to the lowest potential (ground) that influences the threshold voltage via the **body effect**.

<p align="center">
  <img width="3662" height="1453" src="https://github.com/user-attachments/assets/e1dc65f1-f637-4230-8f70-9f466bdd5edb" alt="NMOS Structure" />
</p>

---

### ⚙️ <ins>Working Principle</ins>

1. When **V<sub>GS</sub> = 0**, both drain and source junctions are reverse-biased — the NMOS is **OFF**.  
2. Increasing **V<sub>GS</sub>** attracts electrons toward the gate-oxide interface.  
3. Once **V<sub>GS</sub> ≥ V<sub>T</sub>**, an **inversion channel** forms, allowing current to flow between drain and source.  
4. The drain current (**I<sub>D</sub>**) depends on both **V<sub>GS</sub>** (channel formation) and **V<sub>DS</sub>** (potential difference along the channel).

<p align="center">
  <img src="https://github.com/user-attachments/assets/fc3b4477-4da4-4077-8856-bed78b2d588f" width="600" alt="NMOS Channel Formation" />
</p>

---

### 🧩 <ins>Threshold Voltage & Body Effect</ins>

When a **positive substrate bias** is applied, the depletion region widens, requiring higher gate voltage to form the channel.  
This leads to an **increase in threshold voltage (V<sub>T</sub>)**, known as the **Body Effect**.

\[
V_t = V_{t0} + \gamma \left( \sqrt{|{-2\phi_F + V_{SB}}|} - \sqrt{|{-2\phi_F}|} \right)
\]

<p align="center">
  <img width="1772" height="912" src="https://github.com/user-attachments/assets/e8d51a86-8a7b-4854-9266-20ef361b8a4c" alt="Threshold Voltage Graph" />
</p>

---

### 🔬 <ins>Regions of Operation</ins>

#### 🟢 Resistive (Linear) Region
When **V<sub>DS</sub> < (V<sub>GS</sub> − V<sub>T</sub>)**, the NMOS acts as a **voltage-controlled resistor**.

\[
I_D \approx \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th}) V_{DS}
\]

Effective ON resistance:

\[
R_{on} = \frac{1}{\mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})}
\]

#### 🔵 Saturation (Active) Region
As **V<sub>DS</sub>** increases further, the channel pinches off near the drain end. The MOSFET enters the **saturation region**, where current is mostly independent of V<sub>DS</sub> and controlled by V<sub>GS</sub>.

\[
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2
\]

**Pinch-Off Condition:**

\[
V_{DS(sat)} = V_{GS} - V_{th}
\]

<p align="center">
  <img width="1672" height="887" src="https://github.com/user-attachments/assets/41e6c87f-22f0-425f-838f-12a6d427a0b4" alt="Pinch-Off Condition" />
</p>

---

### 🌊 <ins>Drift Current and Charge Transport</ins>

Electrons move through the inversion layer due to the **electric field** along the channel.  
This is described by the **Drift Current Equation**:

\[
I_D = -v_n(x) \cdot Q_i(x) \cdot W
\]

where  
- \( v_n(x) = \mu_n E(x) \) is the carrier drift velocity, and  
- \( Q_i(x) \) is the mobile charge density per unit area.

This equation forms the basis for deriving MOSFET current-voltage relationships and forms the core of SPICE device modeling.
<img width="1817" height="1018" alt="Screenshot 2025-10-17 145700" src="https://github.com/user-attachments/assets/59e11939-a878-4f49-b4c3-109b510668c6" />

---

### 🧮 <ins>SPICE Simulation Setup</ins>

SPICE uses mathematical device models to replicate transistor behavior.  
The **netlist** defines the components, connections, and parameters, and the simulation engine computes the resulting voltages and currents.

**Common NMOS Parameters in SPICE:**
\[
V_{t0}, \; k_n, \; \gamma, \; \mu_n, \; C_{ox}, \; \frac{W}{L}, \; \lambda
\]
<img width="1841" height="1054" alt="Screenshot 2025-10-18 102642" src="https://github.com/user-attachments/assets/9cc30df1-d012-477c-82ea-343441bfe7f2" />

#### 📘 Example Netlist

```spice
* SPICE Netlist for NMOS Circuit Simulation

M1 vdd n1 0 0 nmos W=1.8u L=1.2u
R1 in n1 55
Vdd vdd 0 DC 2.5  
Vin in 0 DC 2.5

.MODEL nmos NMOS (VTO=0.7 KP=120U GAMMA=0.5)

.OP
.DC Vin 0 2.5 0.01
.PRINT DC V(n1) I(R1)
.END

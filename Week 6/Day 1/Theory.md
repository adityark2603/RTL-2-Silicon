# RISC-V SoC Tapeout Program VSD
## ⛅ Inception of open-source EDA, OpenLANE, and Sky130 PDK
### <ins>Package:</ins>
In any embedded board, what we see as the *chip* is actually its **package** — a protective layer encapsulating the real silicon **die**. The **actual chip (die)** is placed at the center of the package. Electrical connections between the **package** and the **chip** are made using the **Wire Bond** method. <br>

<img width="1891" height="1628" alt="Screenshot 2025-10-26 123444" src="https://github.com/user-attachments/assets/17aff864-58dc-42bf-813c-ff797217fbd9" />


### <ins>Chip Structure:</ins>
1. **Pads**: Interface points for signals entering or leaving the chip.  
2. **Core**: Contains all the digital logic.  
3. **Die**: The combination of *core + pads* — the fundamental manufacturing unit. <br>

<img width="1657" height="1030" alt="image" src="https://github.com/user-attachments/assets/79a213e0-1c86-409c-9b7e-2f3c5098969e" />

#### <ins>Foundry & IPs:</ins>
   - **Foundry**: The manufacturing facility where semiconductor chips are fabricated.  
   - **Foundry IPs**: Proprietary design components optimized for a specific process node.  
   - **Macros**: Reusable digital logic blocks.

<img width="1937" height="1050" alt="image" src="https://github.com/user-attachments/assets/647c4de3-26f1-47de-92b2-f32e6371acfa" />


### <ins> Introduction to RISC-V Instruction Set Architecture:</ins>
A **C program** running on hardware follows a sequence of transformations:

   1. **C Program → Assembly (ISA)**  
      Example: `RISC-V ISA` – *Reduced Instruction Set Computing Architecture*  
   2. **Assembly → Machine Language**  
      Converts to binary (0s and 1s) understood by hardware.  
   3. **RTL Implementation**  
      Hardware logic implementing the ISA using Verilog/VHDL.  
   4. **PnR / RTL-to-GDSII Flow**  
      Converts RTL to layout for chip fabrication.<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d23059f6-8cfa-4396-abcb-b59913073c70" />


### <ins>Software to Hardware Flow:</ins>
#### System Software Layers:
   1. **Operating System (OS)** – Provides basic functions in C, C++, VB, Java.  
   2. **Compiler** – Converts high-level code into hardware-specific instructions.  
   3. **Assembler** – Converts instructions into binary (machine code).

These binaries are then executed by the **hardware**. <br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b8c9db80-2362-4b87-9f76-ebf5bb19aaed" />

### <ins>RTL and Physical Design:</ins>
   1. **Compiler Output** → Instructions  
   2. **Assembler Output** → Binary  
   3. **RTL (Hardware Description Language)** implements instructions  
   4. **Synthesis** → Converts RTL to gate-level netlist  
   5. **Physical Design Implementation** → Layout and fabrication

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b8699379-35e1-4688-b28d-f7382d136a38" /> <br>

### 🌍 7. Open-Source Implementation

#### Open-Source Enablers
1. **RTL Designs**  
2. **EDA Tools**  
3. **PDK Data**

##### Historical Background
- In 1979, **Lynn Conway** and **Carver Mead** introduced structured VLSI design with λ-based design rules.  
- This led to **fabless companies** (design only) and **pure-play fabs** (fabrication only).  
- The interface between the two is defined by **Process Design Kits (PDKs)** containing:  
  - Device Models  
  - Technology Info  
  - Design Rules  
  - Standard Cell Libraries  
  - I/O Libraries  

PDKs were once closed-source (under NDAs), but in **2020**, **Google and Skywater** released the **first open-source PDK (130nm process)**.

📸 *[Insert relevant image]*

---

### 🏗️ 8. ASIC Design Flow

ASIC (Application-Specific Integrated Circuit) design involves multiple stages and tools tied together in a **standardized flow**.

📸 *[Insert flow diagram]*

---

### 🧩 9. OpenLANE ASIC Design Flow

**Goal:** Take a design from **RTL → GDSII** (final layout for fabrication).

📸 *[Insert image]*

#### 🔧 Synthesis
- Converts **RTL** → **Gate-Level Netlist** using **Standard Cell Libraries (SCL)**.  
- Output is functionally equivalent to RTL.

📸 *[Insert image]*

#### 🧱 Standard Cell Views
Each standard cell has multiple representations used by various EDA tools:

| View Type | Description |
|------------|-------------|
| Liberty (.lib) | Electrical and timing models |
| HDL Models | Behavioral simulation |
| SPICE/CDL | Transistor-level simulation |
| GDSII | Detailed physical layout |
| LEF | Abstract layout view |

📸 *[Insert image]*

---

### 🗺️ 10. Floor Planning

#### 🧭 Chip Floor Planning
Defines the overall layout, including placement of macros and I/O pads.

📸 *[Insert image]*

#### 📐 Macro Floor Planning
Places large blocks (like SRAMs, ALUs) inside the core.

📸 *[Insert image]*

---

### ⚡ 11. Power Planning (PP)

- Uses upper metal layers for **power distribution** (thicker = lower resistance).  
- Aims to prevent **electromigration** and **IR drops**.

📸 *[Insert image]*

---

### 📍 12. Placement

#### Global Placement
- Rough placement of cells based on connectivity.  
- Overlaps may occur.

#### Detailed Placement
- Refines placement to ensure legality (non-overlapping).

📸 *[Insert image]*

---

### ⏰ 13. Clock Tree Synthesis (CTS)

- Ensures clock reaches all sequential elements.  
- **Clock Skew**: Time difference in clock arrival at different components.

📸 *[Insert image]*

---

### 🔗 14. Routing

- **Skywater PDK** has **6 routing layers**:  
  - Bottom: Titanium Nitride (Local Interconnect)  
  - Top 5: Aluminum layers

📸 *[Insert stackup image]*

#### Global & Detailed Routing
Performs signal interconnections at metal layers.

📸 *[Insert image]*

---

### ✅ 15. Sign-Off Checks

Before fabrication, the final layout undergoes several verification steps:

| Check | Purpose |
|--------|----------|
| **DRC (Design Rule Check)** | Ensures layout obeys fabrication rules |
| **LVS (Layout vs Schematic)** | Verifies layout matches gate-level netlist |
| **STA (Static Timing Analysis)** | Ensures design meets timing constraints |

📸 *[Insert image]*

---

### 🧩 Summary

| Stage | Description |
|--------|-------------|
| **Package** | Protective covering over the silicon die |
| **Die** | Core + Pads |
| **ISA** | Instruction set architecture (e.g., RISC-V) |
| **RTL Design** | Hardware description implementation |
| **Synthesis** | RTL → Gate-level netlist |
| **PnR Flow** | Physical design and layout generation |
| **OpenLANE** | Open-source ASIC implementation toolchain |
| **Skywater PDK** | Open-source 130nm fabrication process |

---

### 🏁 End of Document
*Author: [Your Name]*  
*Project: Open-Source ASIC Design using RISC-V and OpenLANE*

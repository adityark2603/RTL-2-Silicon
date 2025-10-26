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

### <ins> Open-Source Implementation: </ins>
For **open-source ASIC design implementation**, three key enablers must be readily available as open-source versions: **RTL designs, EDA tools, and PDK data**.
The interface between designers and the fabrication facility has evolved into a collection of data files and documents known as **Process Design Kits (PDKs)**.
These kits include—but are not limited to—**device models, technology information, design rules, digital standard cell libraries, I/O libraries**, and more.

### <ins>OpenLANE ASIC Design Flow:</ins>
ASIC (Application-Specific Integrated Circuit) design involves multiple stages and tools tied together in a **standardized flow**. The goal is to take a design from **RTL → GDSII** (final layout for fabrication), with no human intervention.

<img width="1100" height="779" alt="image" src="https://github.com/user-attachments/assets/15b97734-ac05-4e8f-a0f8-1e1ccf1372bd" />

### <ins>RTL to GDSII Complete Flow:</ins>
<img width="1771" height="955" alt="image" src="https://github.com/user-attachments/assets/13bf9e74-061a-4c36-b594-a5cc4d9b2eca" />

#### 1. <ins>Synthesis:</ins>
   - Converts **RTL** → **Gate-Level Netlist** using **Standard Cell Libraries (SCL)**.  
   - Output is functionally equivalent to RTL.

#### 2. <ins>Floor Planning & Power Planning:</ins>
   - **Chip Floor-Planning** - Partitions the chip die between different system building blocks and places I/O ads
   - **Macro Floor-Planning** - Assigns dimensions, pin locations, and row definitions.
   - **Power Planning** - Performed to minimize issues such as electromigration and IR drops.

#### 3. <ins>Placement:</ins>
   - Involves arranging the standard cells on the chip floorplan to optimize area, performance, and power.
   - It ensures minimal wirelength and efficient signal timing while adhering to design constraints and block boundaries.

#### 4. <ins>Clock-Tree Synthesis (CTS):</ins>
   - CTS builds a balanced clock distribution network that delivers the clock signal to all sequential elements with minimal skew and latency.
   - It ensures synchronization across the chip while maintaining timing and power efficiency.

#### 5. <ins>Routing:</ins>
   - Routing connects all the placed cells, pins, and macros using metal layers while adhering to design rules.
   - It focuses on minimizing congestion, delay, and crosstalk to ensure reliable signal propagation.

#### 6. <ins>Sign-Off:</ins>
   - Sign-off is the final verification stage before tape-out, ensuring the design is ready for fabrication. 
   - It includes **Design Rule Check (DRC)** to validate layout rules, **Layout vs. Schematic (LVS)** to confirm connectivity, and **Static Timing Analysis (STA)(( to verify that timing constraints are met.


# RISC-V SoC Tapeout Program VSD
## 🗺️ OpenROAD Flow Setup and Floorplan + Placement
OpenROAD is the core application and the engine of the flow. It is a unified executable that performs the actual physical design work.

### 🏗️ <ins>Floorplanning</ins>
Floorplanning is the process of **allocating space**, determining the **shape and size of the chip**, and defining the **precise locations of major functional blocks** (macros, I/O pads, etc.) before placing standard cells (logic gates).

#### <ins>Key Components:</ins>
1. **Die Area:**
  The total physical area of the silicon chip.
2. **Core Area:**
  The inner region where all logic (standard cells and macros) is placed.
  **Core Utilization:** Usually 70%-85%, defined as the ratio of standard cell area to the available core area.
3. **I/O Pad / Pin Placement:**
  Placed around the periphery of the die to interface the chip with the outside world.
4. **Macro Placement:**
  Large pre-designed blocks like SRAM, PLLs, or custom IP.
5. **Placement Strategy:**
    - Close to connected logic to minimize wire length (**flylines**)
    - Avoid congestion and routing conflicts
6. **Standard Cell Rows:**
  The core area is divided into horizontal rows where standard cells (basic logic gates) are placed and powered.
7. **Power Planning (PDN):**
  Critical for delivering stable power. Includes a grid of thick metal straps (VDD & GND). Poor PDN design leads to **IR drop** and timing failures.
8. **Physical-Only Cells:**
      - **Tap Cells:** Maintain substrate integrity and prevent latch-up
      - **Endcaps:** Placed at the ends of rows
      - **Blockages:** Reserve areas for future logic or avoid congestion near macros


### 🧩 <ins>Placement</ins>

Placement is the process of arranging **standard cells** and smaller blocks within the core area defined during floorplanning.

#### <ins> Objectives:</ins>

* **Minimize Wire Length:** Place connected cells close together for faster signals and lower power.
* **Reduce Congestion:** Avoid overcrowding to simplify routing.
* **Meet Timing:** Ensure signal paths meet the required clock cycle constraints.

#### <ins>Required Files for Placement:</ins>

* **Floorplan DEF/ODB:** Output from floorplanning defining core area, rows, macros, and I/O pins
* **Synthesized Netlist (.v):** Describes standard cells and their connections
* **Libraries (.lef, .lib):** LEF provides cell shapes, LIB provides timing information

### 🪜 <ins>Stages of Placement:</ins>
1. **Global Placement:**
   * Find approximate locations for all standard cells to minimize wire length (HPWL metric).
   * Uses algorithms like **quadratic placement** or **partitioning**.
   * Cells may overlap and are not fully aligned to rows.

2. **Detailed Placement:**
   * Snap cells to standard cell rows defined in the floorplan.
   * Remove overlaps and adhere strictly to placement grids and design rules.
   * Maintain wire length optimization from global placement.

#### <ins>📊 Process Flow:</ins>
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/4bcd3b87-104d-4a2a-a5da-41ab5f003bdc" />


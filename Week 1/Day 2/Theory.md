# RISC-V SoC Tapeout Program VSD
## Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding ✨



### ☁️ <ins>SKY130 PDK Overview:</ins> 

The SKY130 PDK is an open-source Process Design Kit based on SkyWater Technology's 130nm CMOS technology. It provides essential models and libraries for integrated circuit (IC) design, including timing, power, and process variation information.


**File Name:** `sky130_fd_sc_hd__tt_025C_1v80.lib`

**Naming Convention Breakdown:**
- `tt` → typical-typical corner
- `025C` → 25°C temperature  
- `1v80` → 1.8V supply


<br>

<img width="3840" height="1741" alt="Screenshot (28)" src="https://github.com/user-attachments/assets/4c211c4a-0b7a-426a-8e11-073846571cc4" />



---

### 🏆 NAND vs NOR Implementation

| Aspect              | NAND Gate                          | NOR Gate                          | Advantage                          |
|---------------------|------------------------------------|-----------------------------------|------------------------------------|
| Transistor Efficiency | PDN (NMOS) in series, PUN (PMOS) in parallel | PDN (NMOS) in parallel, PUN (PMOS) in series | NAND - Faster, smaller, better PMOS arrangement |
| Speed               | Shorter propagation delay          | Delay worsens with fan-in (series PMOS) | NAND - Better scalability          |
| Power Consumption   | Lower static & dynamic power       | Higher capacitance from series PMOS | NAND - More power-efficient        |
| Universality        | Universal gate                     | Universal gate                    | Equal                              |
| Practical Usage     | Preferred in fabrication           | Less preferred                    | NAND - Better CMOS performance     |
| Memory Applications | NAND Flash: High density, low cost | NOR Flash: Faster random access   | NAND - Dominates for storage       |


***Abbreviations:** PDN = Pull-Down Network, PUN = Pull-Up Network*

---



###  ❓Why is Submodule Synthesis Needed?

- Breaks large designs into manageable blocks
- Reduces tool runtime and complexity
- Pre-optimized modules (ALU, FIFO, decoder) can be reused across projects
- Easier to test and pinpoint issues in smaller blocks
</br>

### ❓Why are Flip-Flops Essential?
- They provide memory capability, allowing circuits to remember past states for sequential logic operations.
- They synchronize all circuit operations to clock edges, preventing timing errors and race conditions.
- They enable pipelining and glitch filtering by breaking long combinational paths and ensuring stable data sampling.
</br>

### ❓What is a Glitch?
- Unwanted short pulse caused by different path delays in combinational logic
- **Danger:** Can trigger unintended events in combinational systems
- **Solution:** Flip-flops filter glitches by sampling only at clock edges

---
## Hierarchical vs. Flattened Synthesis
### ✒️ <ins>Hierarchical Synthesis:</ins>
- **Definition**: Retains the module hierarchy as defined in RTL, synthesizing modules separately.
- **How it Works**: Tools like Yosys process each module independently, using commands such as `hierarchy` to analyze and set up the design structure.

**Advantages:**
- Faster synthesis time for large designs.
- Improved debugging and analysis due to maintained module boundaries.
- Modular approach, aiding integration with other tools.

**Disadvantages:**
- Cross-module optimizations are limited.
- Reporting can require additional configuration.

### ✒️ <ins>Flattened Synthesis:</ins>
- **Definition**: Merges all modules into a single flat netlist, eliminating hierarchy.
- **How it Works**: The `flatten` command in Yosys collapses the hierarchy, allowing whole-design optimizations.

**Advantages:**
- Enables aggressive, cross-module optimizations.
- Results in a unified netlist, sometimes simplifying downstream processes.

**Disadvantages:**
- Longer runtime for large designs.
- Loss of hierarchy complicates debugging and reporting.
- Can increase memory usage and netlist complexity.

---
### **📝 <ins> D Flip-Flop Applications</ins>**: 
#### 1. In Combinational Circuits
- Output synchronization to a clock edge
- Glitch filtering at the final output stage
- Pipeline stage insertion for timing optimization

#### 2. In Sequential circuits
- State storage for finite state machines
- Data storage in registers and memory elements
- Synchronization element in counters and shift registers


### **📝 <ins> D Flip-Flop Types</ins>**: 
#### 1. Synchronous (Syn) DFF
- Definition: Input changes affect output only at clock edges
- Usage: Registers, pipelines, counters, state machines
- Timing: Tsetup, Thold, Tcq
- Advantages: Predictable, easy to analyze, eliminates race conditions

#### 2. Asynchronous (Async) DFF  
- Definition: Output changes via external signals (reset/preset), ignoring clock
- Usage: Counter reset, register initialization, interrupt handling
- Characteristics: Immediate response, potential timing hazards
- Advantages: Fast control response
- Disadvantages: Metastability risk, harder timing control






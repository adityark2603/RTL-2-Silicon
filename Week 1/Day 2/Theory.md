# RISC-V SoC Tapeout Program VSD
## Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding ✨



### <ins>SKY130 PDK Overview:</ins>

The SKY130 PDK is an open-source Process Design Kit based on SkyWater Technology's 130nm CMOS technology. It provides essential models and libraries for integrated circuit (IC) design, including timing, power, and process variation information.


**File Name:** `sky130_fd_sc_hd__tt_025C_1v80.lib`

**Naming Convention Breakdown:**
- `tt` → typical-typical corner
- `025C` → 25°C temperature  
- `1v80` → 1.8V supply


<br>

<img width="3840" height="1741" alt="Screenshot (28)" src="https://github.com/user-attachments/assets/4c211c4a-0b7a-426a-8e11-073846571cc4" />



---

## 🏆 NAND vs NOR Implementation


| Aspect | NAND Gate | NOR Gate | Advantage |
|--------|-----------|----------|-----------|
| **Transistor Efficiency** | Pull-down (NMOS) in series<br>Pull-up (PMOS) in parallel | Pull-down (NMOS) in parallel<br>Pull-up (PMOS) in series | **NAND** - Faster, smaller, better PMOS arrangement |
| **Speed** | Shorter propagation delay | Delay worsens with increased fan-in (series PMOS) | **NAND** - Better scalability with input size |
| **Power Consumption** | Less static and dynamic power | Higher capacitance from series PMOS | **NAND** - More power efficient |
| **Universality** | Universal gate | Universal gate | **Equal** - Both can implement any Boolean function |
| **Practical Usage** | Preferred in fabrication | Less preferred | **NAND** - Better performance in CMOS |
| **Memory Applications** | NAND flash: higher density, lower cost, lower power | NOR flash: faster random access | **NAND** - Dominates market for density/cost |



---



### ❓ *Why is Submodule Synthesis Needed?*

- Breaks large designs into manageable blocks
- Reduces tool runtime and complexity
- Pre-optimized modules (ALU, FIFO, decoder) can be reused across projects
- Easier to test and pinpoint issues in smaller blocks
- Change one module without resynthesizing entire chip
- Saves time in iterative design cycles
- Different constraints per module (speed vs area optimization)
- Third-party IPs provided as pre-synthesized netlists

---



### ❓ *Why are Flip-Flops Essential?*
- Store 1 bit of data enabling sequential circuits
- Examples: counters, registers, processors
- Capture data only on clock edges
- Prevents race conditions
- Pipelining improves maximum operating frequency
- Cuts long delays into manageable stages

---



### ❓ *What is a Glitch?*
- Unwanted short pulse caused by different path delays in combinational logic
- **Danger:** Can trigger unintended events in combinational systems
- **Solution:** Flip-flops filter glitches by sampling only at clock edges

---

## Flip-Flop Timing Parameters

### 🔹 Key Delays in Flip-Flops

| Parameter | Description | Importance |
|-----------|-------------|------------|
| **Setup Time (Tsetup)** | Input must be stable before clock edge | Prevents metastability |
| **Hold Time (Thold)** | Input must remain stable after clock edge | Ensures proper capture |
| **Clock-to-Q Delay (Tcq)** | Output delay after clock edge | Defines propagation timing |

**⚠️ Violations cause metastability (unpredictable output)**

---

## Flip-Flop Applications

### 🔹 1. In Combinational Circuits
- **Synchronize Outputs:** Ensure stable outputs at clock edges
- **Glitch Prevention:** Filter unwanted transitions
- **Pipelining:** Break long paths into stages (e.g., 32-bit adder → 8-bit stages)

### 🔹 2. In Sequential Circuits
- **State Storage:** Memory for counters, FSMs, shift registers
- **Synchronization:** Clocked operation prevents race conditions
- **Stability:** Prevent oscillations in feedback paths

---

## D Flip-Flop Types

### 🔹 2. Synchronous (Syn) DFF
- **Definition:** Input changes affect output only at clock edges
- **Usage:** Registers, pipelines, counters, state machines
- **Timing:** Tsetup, Thold, Tcq
- **Advantages:** Predictable, easy to analyze, eliminates race conditions

### 🔹 3. Asynchronous (Async) DFF  
- **Definition:** Output changes via external signals (reset/preset) ignoring clock
- **Usage:** Counter reset, register initialization, interrupt handling
- **Characteristics:** Immediate response, potential timing hazards
- **Advantages:** Fast control response
- **Disadvantages:** Metastability risk, harder timing control

---

## Key Takeaways

### 🎯 Summary
- **NAND gates** are preferred over NOR for better performance in CMOS
- **Submodule synthesis** enables scalable, reusable, and manageable design flow
- **Flip-flops** are crucial for state storage, synchronization, and timing control
- **Glitches** are filtered by clocked flip-flop sampling
- **Synchronous DFFs** provide predictable timing for most sequential designs
- **Asynchronous DFFs** offer immediate control but require careful handling


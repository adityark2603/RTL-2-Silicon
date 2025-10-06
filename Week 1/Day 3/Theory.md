# ⚙️ RISC-V SoC Tapeout Program – VSD  
## 🔭 Combinational & Sequential Optimizations  
### 💡 <ins>Logic Circuits</ins>  
### Combinational Circuits  
- Time-independent circuits — outputs depend **only on current inputs**.  
- No memory — do not depend on previous input values.  

### Sequential Circuits  
- Time-dependent — outputs depend on **both present and past inputs**.  
- Require **clock cycles** since they have memory elements.  



## 🧠 Introduction to Logic Optimizations  
Logic optimization is crucial to:  
-  Reduce total logic area  
-  Lower power consumption  
-  Improve overall circuit performance  



## ⚡ Combinational Logic Optimization  

### Why Optimize Combinational Logic?  
- Squeezing the logic (removing redundancies) results in a more efficient design, saving **area and power**.  

### 🧮 Types of Combinational Optimizations  
-  **Constant Propagation**  
-  **Boolean Logic Optimization**  
  - Karnaugh Map (K-map)  
  - Quine-McCluskey Method  



### 🔢 Constant Propagation  
Inputs that do not influence the output are ignored or replaced to simplify the logic, saving area and power.  

#### 🧠 Example  
Given the logic function:  

`Y = ((AB) + C)'`

If `A = 0`:  
`Y = ((0) + C)' = C'`

👉 Here, **A can be removed** since it does not affect the output.  

---

### 🔣 Boolean Logic Optimization  

Simplify complex Boolean expressions using the laws of Boolean algebra.  

#### Example  

**Given:**  

**Stepwise Simplification:**  
y = a'c' + a(bc + b'ca)
  = a'c' + abc + ab'c
  = a'c' + ac(b + b')
  = a'c' + ac
  = a ⊕ c



**Final Simplified Result:**  
`y = a ⊕ c`


---

## 🕒 Sequential Logic Optimization  

### ⚙️ Types of Sequential Optimizations  

#### 🔸 Basic Technique  
- **Sequential Constant Propagation**  

#### 🔹 Advanced Techniques  
- **State Optimization**  
- **Retiming**  
- **Sequential Logic Cloning (Floorplan-aware synthesis)**  



### 🧠 Sequential Constant Propagation  
Like combinational logic, redundant or constant signals within sequential logic can simplify **state machines** or **latches**.  



### 🧩 State Optimization  
- Minimizes the number of states in **Finite State Machines (FSMs)**.  
- Removes **unreachable** or **equivalent states** to improve efficiency.  



### ⏱️ Retiming  
- Restructures the placement of **registers (flip-flops)** across logic without changing functionality.  
- Used to **meet timing** or **area constraints**.  


### 🧬 Sequential Logic Cloning  
- Duplicates logic based on **floorplanning** to improve **locality** and **reduce routing delays**.  
- Typically performed during **physical layout planning**.  


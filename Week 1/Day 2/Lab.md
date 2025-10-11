# RISC-V SoC Tapeout Program VSD
## ✨ Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding 
## 📊 <ins>Hierarchical vs Flat Synthesis</ins> 
### <ins>**Multiple Module Synthesis:**</ins>
``` bash
$ gvim multiple_modules.v
```

#### Code:

![WhatsApp Image 2025-09-27 at 07 43 02_3344ec23](https://github.com/user-attachments/assets/7b105db2-c508-4a23-800b-3e17731b0869)

#### **Synthesized view of Multiple modules:**
```bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky_130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog multiple_modules.v
$ synth -top multiple_modules
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky_130_fd_sc_hd__tt_025C_1v80.lib
$ show multiple_modules
```
#### Output:

![WhatsApp Image 2025-09-27 at 07 51 23_7e475f19](https://github.com/user-attachments/assets/44e381f4-93f0-4485-b518-6ac119c7c7b0)

#### **Hierarchial Netlist:**
``` bash
$ write_verilog -noattr multiple_modules_hier.v
$ !gvim multiple_modules_hier.v
```

#### Code:

![WhatsApp Image 2025-09-27 at 07 53 55_f6de60cf](https://github.com/user-attachments/assets/5d07d222-2b4a-48c0-b0c0-8166d2630f81)

#### **Flattened Synthesis view of Multiple modules:**
``` bash
$ flatten
```

#### Output:

![WhatsApp Image 2025-09-27 at 08 31 20_86215c09](https://github.com/user-attachments/assets/23ce9998-2f03-4875-9a9a-9309ca9d4530)


### <ins>**Sub-Module Synthesis:**</ins>
``` bash
$ synth -top sub_module
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky_130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### Output:

![WhatsApp Image 2025-09-27 at 08 36 13_34c08963](https://github.com/user-attachments/assets/f6673b31-3340-48b2-99e1-9bba45b0f3f0)

## <ins>Types of D Flip-Flops:</ins>
### 1. Asynchronous Reset D Flip-Flop:

```verilog
module dff_asyncres (input clk, input async_reset, input d, output reg q);
  always @ (posedge clk, posedge async_reset)
    if (async_reset)
      q <= 1'b0;
    else
      q <= d;
endmodule
```
- **Asynchronous reset**: Overrides clock, setting q to 0 immediately.
- **Edge-triggered**: Captures on rising clock edge if reset is low.

### 2. Asynchronous Set D Flip-Flop:

```verilog
module dff_async_set (input clk, input async_set, input d, output reg q);
  always @ (posedge clk, posedge async_set)
    if (async_set)
      q <= 1'b1;
    else
      q <= d;
endmodule
```
- **Asynchronous set**: Overrides clock, setting q to 1 immediately.

### 3. Synchronous Reset D Flip-Flop:

```verilog
module dff_syncres (input clk, input async_reset, input sync_reset, input d, output reg q);
  always @ (posedge clk)
    if (sync_reset)
      q <= 1'b0;
    else
      q <= d;
endmodule
```
- **Synchronous reset**: Takes effect only on the clock edge.

### ⚡<ins>iverilog Simulation Results:</ins> 
#### 1. Asynchronous Reset D Flip-Flop:
``` bash
$ iverilog dff_asyncres.v tb_dff_asyncres.v
$ ./a.out
$ gtkwave tb_dff_asyncres.vcd
```

#### Output:

![WhatsApp Image 2025-09-27 at 09 08 22_85533f50](https://github.com/user-attachments/assets/80a4d386-46e6-4f59-802c-f8855552bb41)

#### 2. Asynchronous Set D Flip-Flop:
``` bash
$ iverilog dff_async_set.v tb_dff_async_set.v
$ ./a.out
$ gtkwave tb_dff_async_set.vcd
```

#### Output:

![WhatsApp Image 2025-09-27 at 09 11 51_f51082f4](https://github.com/user-attachments/assets/cefba9a0-a276-47e3-a1b5-ded2b20336a1)

#### 3. Synchronous Reset D Flip-Flop:
``` bash
$ iverilog dff_syncres.v tb_dff_syncres.v
$ ./a.out
$ gtkwave tb_dff_syncres.vcd
```
#### Output:

![WhatsApp Image 2025-09-27 at 09 17 16_e0a5309c](https://github.com/user-attachments/assets/4f12cc1e-a069-495d-9403-c40ea2dc655d)


### 🖋️<ins>Synthesis with Yosys:</ins> 
#### 1. Asynchronous Reset D Flip-Flop:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_asyncres.v
$ synth -top dff_asyncres
$ dfflibmap -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### Output:

![WhatsApp Image 2025-09-27 at 12 17 41_a1a3d8c0](https://github.com/user-attachments/assets/c76d9dd5-fa03-41d2-a07c-4ef8f59090c6)

#### 2. Asynchronous Set D Flip-Flop:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_async_set.v
$ synth -top dff_async_set
$ dfflibmap -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### Output:

![WhatsApp Image 2025-09-27 at 12 22 06_e23ce0b4](https://github.com/user-attachments/assets/01d94b54-67c3-4ef1-acf9-006538455421)

#### 3. Synchronous Reset D Flip-Flop:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_syncres.v
$ synth -top dff_syncres
$ dfflibmap -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### Output:

![WhatsApp Image 2025-09-27 at 12 24 26_6ef0528d](https://github.com/user-attachments/assets/091b0e9b-6754-4b29-b0a8-e994c804ba2f)


### 🧮 <ins>Interesting Optimization cases:</ins>
``` bash
$ gvim mult_*.v -o
```

#### Code:

<img width="1795" height="750" alt="image" src="https://github.com/user-attachments/assets/0b59d800-40f6-42d3-829e-80a96e330ffc" />

### <ins>mul2</ins>:
```bash
$ yosys
$ read_liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog mult_2.v
$ synth -top mul2
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### Output:

![WhatsApp Image 2025-09-27 at 12 35 16_461a89af](https://github.com/user-attachments/assets/b54abfbb-b416-4ffe-9f1d-1614d0d5ef00)

#### Netlist:
```bash
$ write_verilog -noattr mul2_net.v
$ !gvim mul2_net.v
```

#### Code:

<img width="1792" height="854" alt="image" src="https://github.com/user-attachments/assets/727bc0dc-ee68-4d61-abce-d413d7398484" />



### <ins>mul8</ins>:
```bash
$ yosys
$ read_liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog mult_8.v
$ synth -top mult8
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### Output:

![WhatsApp Image 2025-09-27 at 12 40 27_4e854a28](https://github.com/user-attachments/assets/2061b075-aaa5-413a-925f-2a0a354f4ebc)

#### Netlist:
```bash
$ write_verilog -noattr mult8_net.v
$ !gvim mult8_net.v
```

#### Code:

<img width="1795" height="855" alt="image" src="https://github.com/user-attachments/assets/acebbf72-f9a1-4aef-bff0-bd7c531e08a1" />





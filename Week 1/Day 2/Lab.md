# RISC-V SoC Tapeout Program VSD
## Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding ✨
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

**Output:**

![WhatsApp Image 2025-09-27 at 09 08 22_85533f50](https://github.com/user-attachments/assets/80a4d386-46e6-4f59-802c-f8855552bb41)

#### 2. Asynchronous Set D Flip-Flop:
``` bash
$ iverilog dff_async_set.v tb_dff_async_set.v
$ ./a.out
$ gtkwave tb_dff_async_set.vcd
```

**Output:**

![WhatsApp Image 2025-09-27 at 09 11 51_f51082f4](https://github.com/user-attachments/assets/cefba9a0-a276-47e3-a1b5-ded2b20336a1)

#### 3. Synchronous Reset D Flip-Flop:
``` bash
$ iverilog dff_syncres.v tb_dff_syncres.v
$ ./a.out
$ gtkwave tb_dff_syncres.vcd
```
**Output:**

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

**Output:**

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

**Output:**

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

**Output:**

![WhatsApp Image 2025-09-27 at 12 24 26_6ef0528d](https://github.com/user-attachments/assets/091b0e9b-6754-4b29-b0a8-e994c804ba2f)



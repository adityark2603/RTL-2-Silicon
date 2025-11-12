# RISC-V SoC Tapeout Program VSD
## 🎨 Design Library cell using Magic Layout & NGSpice Characterization
### <ins>SPICE Deck creation for CMOS Inverter:</ins>
A SPICE deck is a text file used for circuit simulation that lists all circuit elements (like resistors, transistors, capacitors) with their connections, values, and the nodes that link them together. <br>

<img width="1747" height="820" alt="image" src="https://github.com/user-attachments/assets/c34a1eaf-b5be-4f60-9b41-c36f788a0351" /> <br>

<img width="1720" height="835" alt="image" src="https://github.com/user-attachments/assets/6bf15924-6230-42b3-bed8-2800e19f487c" /> <br>

### <ins>16-Mask CMOS Process:</ins>
#### 1. **<ins>Selecting a substrate:</ins>**
   - The substrate acts as the foundational layer upon which transistors and other components are built
   - Substrate doping should be less than 'well' doping.
     
#### 2. **<ins>Creating an active region for transistors:</ins>**
   - The active region is formed in specific areas of the substrate where the transistor's source, drain, and channel will be created.
   - This is accomplished by defining regions on the silicon wafer through processes such as oxidation, doping (adding impurities), and photolithography to selectively modify conductivity in those areas

<img width="1500" height="757" alt="image" src="https://github.com/user-attachments/assets/91d98d77-74ff-49a6-8289-8b19aaaaaa15" /> <br>

#### 3. **<ins>Local Oxidisation of Silicon:</ins>**
   - In LOCOS, a silicon wafer is selectively oxidized by masking the regions where devices will be formed, then growing a thick silicon dioxide (field oxide) in non-active areas to electrically separate adjacent devices.
   - The bird's beak in LOCOS is the tapered, encroaching shape of the silicon dioxide field oxide that grows laterally under the nitride mask during local oxidation. <br>
   
<img width="1447" height="675" alt="image" src="https://github.com/user-attachments/assets/04694245-41b9-40a4-b3b9-35ff176943b0" />

#### 4. **<ins>Formation of N-well and P-well:</ins>**
   - The process includes oxidation to grow SiO2 layers, photolithography for masking the well areas, ion implantation to dope the wells, annealing to activate the dopants, and subsequent steps for transistor gate, source, and drain formation <br>

<img width="1397" height="775" alt="image" src="https://github.com/user-attachments/assets/88a1b910-8335-4cf9-ab91-80150775c617" /> <br>

#### 5. **<ins>Formation of Gate Terminal:</ins>**
   - A thin layer of gate oxide (SiO2) is thermally grown on the silicon substrate, which acts as the insulating layer for the gate.
   - A layer of polysilicon is then deposited over the oxide, patterned using photolithography, and etched to form the gate electrode, serving as the control terminal for the transistor.

<img width="1627" height="637" alt="image" src="https://github.com/user-attachments/assets/aff2c258-17b5-4d8f-8176-4a6166d5ca56" />

#### 6. **<ins>Lightly Doped Drain Formation:</ins>**
   - Lightly Doped Drain (LDD) formation begins by implanting a lightly doped impurity region adjacent to the transistor gate using the gate as a mask, reducing the electric field near the drain edge and mitigating hot carrier effects.
   - After forming this region, sidewall spacers are created by depositing and etching a conformal layer around the gate edges; these spacers serve as a mask for subsequent heavy doping of the source and drain regions, completing the LDD structure.

📕 **<ins>NOTE:</ins>**
1. **Plasma Anisotropic Etching** - It's a dry etching technique used in semiconductor manufacturing where ions generated in a plasma are directionally accelerated toward the substrate to etch material primarily in a vertical direction. This produces highly controlled, vertical sidewalls with minimal lateral etching, essential for fabricating precise micro- and nanoscale features. <br>

2. **Hot Electron Effect** - Occurs in MOSFETs when electrons gain high kinetic energy near the drain due to strong electric fields, causing impact ionization and injection of electrons into the gate oxide. This leads to gate oxide damage, threshold voltage shift, and reduced transistor lifetime. <br>

3. **Short Channel Effect** - As transistor channel length decreases, the control of the gate over the channel diminishes, causing threshold voltage reduction, increased leakage currents, drain-induced barrier lowering (DIBL), and degradation of device performance. This effect limits device scaling. <br>

#### 7. **<ins>Source and Drain Formation:</ins>**
   - Source and drain formation involves doping specific regions on the silicon substrate by ion implantation or diffusion to create highly doped n+ or p+ areas adjacent to the transistor channel.
   - These regions serve as the terminals for current flow, enabling electron or hole injection when the transistor is operational.
  
<img width="1185" height="505" alt="image" src="https://github.com/user-attachments/assets/b37ddb60-0d17-44fa-a584-d6ec6eddec23" />

#### 8. **<ins>Steps to form contacts & interconnects:</ins>**
   - Etch thin oxide in HF solution
   - Deposit titanium on the wafer surface, using sputtering
   - Wafer heated at about $$650 - 700\^\circ \text{C}$$ in N₂ ambient for 60s

<img width="1162" height="615" alt="image" src="https://github.com/user-attachments/assets/761007ae-37a7-443b-bd22-a598de83bbab" />

#### 9. **<ins>Higher level metal formation:</ins>**
   - 1 micrometer of SiO₂ doped with phosphorus or boron is deposited on the wafer surface
   - Chemical mechanical polishing (CMP) technique for planarizing the wafer surface
  
<img width="1215" height="940" alt="image" src="https://github.com/user-attachments/assets/8f2d2013-5dd0-4542-8e48-dd619ffdb51e" /> <br>

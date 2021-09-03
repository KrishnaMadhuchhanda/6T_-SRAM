

### Design of 6T_SRAM Cell in 0.5um SCMOS Technology.

#### Table of Contents:
 - [6T SRAM DESIGN](#6T_SRAM_DESIGN) 
  - [MODES OF OPERATIONS](#Modes_of_operations)
  -  [PRELAYOUT SIMULATION](#PRE_LAYOUT_SIMULATION)
     - [STATIC NOISE MARGIN (SNM)](#STATIC_NOISE_MARGIN)
     - [TRANSIENT_ANALYSIS](#TRANSIENT_ANALYSIS)
      - [SENSE AMPLIFIER](#Sense_amplifier)
      - [WRITE DRIVER](#Write_Driver)
      - [ Transient Simulation of 6T-SRAM cell with sense amplifier and write driver](#Transient_Simulation_of_6T_SRAM_cell_with_sense_amplifier_and_write_driver)
   - [Transistor Sizing](#Transistor_Sizing)
  - [Future work](#Future_work)
   - [Acknowledgement](#Acknowledgement) 
    
### 6T SRAM DESIGN:
The project is mainly based on the design of full CMOS SRAM (1K*32bit) 6T_SRAM memory design.
#### SRAM:
SRAM(Static Read Access Memory) is a volatile memory i.e data is lost when power is removed. the data and information stored in transistors requires a constant flow of a power due to continuous need of power. SRAM doesn't have to periodically refreshed because it doesn't demand change in action to keep its data intact. 
- Specifications:
   Memory Size - 1k*32-bit,  Technology file - 0.5um SCMOS Technology, Operating voltage - 5V
- Block diagram and circuit diagram of 6T SRAM Cell:
![BLOCK DIAGRAM](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/SRAM_BLOCKDIAGRAM.png) ![CKT DIAGRAM OF SRAM](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/sramnew%20%282%29.png)

### Modes of Operations:
![FIG-A(READ OPERATION)](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/SRAM_READ2.png) FIG-A (READ_OPEARTION) ![FIG-B WRITE OPERATION](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/SRAM_WRITE2.png)
FIG-B(WRITE_OPERATION)

- Read Operation:
   Fig A refers to read operation and In this state initially the bit lines (BL &BLB) are precharged with Vdd,  word line and V2 is connected to Vdd and V1 = 0V value. The main aim of the design for this data read operation is to keep the V1 voltage less than the thresold voltage of the M2 transistor which ensures that the M2 transistor will be turned off during the read operation. M1 transistor will be in linear region and M3 will be in saturation region.
  By solving the Id equation of the respective transistor M1 and M3 we can get the equation(1) as:                                                     
![Equation will be:](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/Eq-1.jpeg)
 
   After putting the values of all typical mos parameters( V1 as Vtn=0.49) we can get the design constraint
   w1/w3 < 0.258
   
- Write Operation:
Fig -B refers to write operation and In this state BL is forced to logic 0 and BLB & WL is connected to Vdd.  V1=Vdd and V2 = 0V.  Here to change the stored information, the node voltage V1 must be reduced below the thresold voltage of M2 so that M2 turns off first.
When V1=Vtn, the transistor M3 will be in linear region while M5 will be in saturation.
By solving the Id equation of M5 & M3 we can get the equation(2) as:

![Equation will be:](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/Eq-2.jpeg)

After putting the typical mos parameters values(V1=Vtn=0.49, Vtp=-0.66) in the equation 2, the generated equation will be:
w5/w3 < 0.654

### Pre-layout Simulation: 
   #### SNM (Static Noise Margin):
  It helps to know the stability of the SRAM cell. It is the lowest voltage noise that can flip the state of the SRAM cell and it can be obtained by plotting the butterfly curve(it is the curve between two voltage transfer characteristics of the two respective converter) and by finding the maximum possible square between them and the length of the sides gives SNM. Greater SNM leads to better stability.
        - HNM(HOLD_NOISE_MARGIN):
   In this state word line is absent and the SRAM will store the previous data.
   ![SNM_HOLD](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/holdnew.png)

   - RNM(READ_NOISE_MARGIN):
    In this state the read margin is used to find the read stability. Read stability is the ability to prevent the SRAM cell to flip the stored value while stored value is being read.
    ![RNM](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/readnew%20%282%29.png)

#### TRANSIENT ANALYSIS:
 ![TRANSIENT CKT DIAGRAM](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/tran%20ckt%20diagram%20%282%29.png)

In the above circuit diagram consists of SRAM_6T cell with all its parasitics, precharged circuit, sense amplifier and write driver. Here the the SRAM size is 1k*32 bit, so the no of rows and column can be taken as 128 no of rows and 256 no of column. Here the parasitic capacitor of 6T SRAM such as word line wire load capacitance  and bit line, bit line bar wire load capacitance are connected to the above circuit diagram and these individual capacitances are of 10f. The mosfets (	M9,M8 & M6,M7) which are present in the above circuit diagram is parasitic mosfet which is likely do the operation like 1k*32 bit cell.

The resulted output is given below:
![output](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/main%20trans%20%282%29.png)

#### SENSE_AMPLIFIER:
Its a differential circuit amplifier which acts as a comparator and senses the voltage difference between bit line and bit line bar and used to detect the node voltage stored in the memory during the read operation.

  ![SENSE_AMPLIFIER CKT DIAGRAM](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/SENSE_AMPLIFIER_SRAM.png)

#### WRITE_DRIVER:
The write driver is used to drive the input signal into the into the bit cell during a write operation.

![WRITE_DRIVER CKT DIAGRAM](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/SRAM_WRITEDRIVER.png)

#### SIMULATION OF 6T SRAM CELL WITH SENSE_AMPLIFIER & WRITE_DRIVER:

![SIMULATION RESULT](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/final%20trans%20with%20sa%20and%20wd.png)

#### Transistor Sizing:
Typical MOS parameters values which i have taken for the calculation purpose
   
 - NMOS: Vt0=0.49V, un=445 cm^2/Vs
 - PMOS: Vt0=-0.66V, up=151 cm^2/Vs
 - Vdd= 5V
 - Wmin= 0.6um, Lmin=0.4um
 
 #### Acknowledgements:
-   Dr.Saroj Rout,Associate Professor,Silicon Institute Of Technology,Bhubaneswar
-   Mr.Santunu Sarangi,Assistant Professor,Silicon Institute Of Technology,Bhubaneswar
#### Contact Information:
- KrishnaMadhuChhanda Panda, Design Engineer,[Sevya Multimedia Technologies Pvt.Ltd](http://sevyamultimedia.com)
- [krishna.panda619@gmail.com](mailto:krishna.panda619@gmail.com) 
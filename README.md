


### Design of 6T_SRAM.

#### Table of Contents:
 - [Introduction](#Introduction)
 - [Transistor Sizing](#Transistor_Sizing)
 - [Modes of Operations](#Modes)
    - [Read](#Read)
     - [Write](#Write)
  - [Pre-layout Simulation](#Prel-layout_Simulation):
     - [DC_Analysis](#DC_Analysis) 
    - [SNM Hold](#SNM_HOLD)
    - [SNM Read](#SNM_READ)
    
#### Introduction:
The project is based on the design of full CMOS SRAM (1K*32bit) 6T_SRAM memory design.
  
 - Specifications:
     - Memory size- 1k*32bit
    - Supply Voltage- 5V
    - Technology- 0.5um SCMOS Technology
  
#### Transistor Sizing:
Typical MOS parameters:
   
 - NMOS: Vt0=0.49V, un=445 cm^2/Vs
 - PMOS: Vt0=-0.66V, up=151 cm^2/Vs
 - Vdd= 5V
 - Wmin= 0.6um, Lmin=0.4um
  ![Schematic of 6T SRAM cell:](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/sram%20%282%29.png)

#### Modes of Operations:

  #### Read Operation:
      In this state initially the bit lines (BL &BLB) are precharged with Vdd,  word line and V2 is connected to Vdd and V1 = 0V value. The main aim of the design for this data read operation is to keep the V1 voltage less than the thresold voltage of the M2 transistor which ensures that the M2 transistor will be turned off during the read operation. M1 transistor will be in linear region and M3 will be in saturation region.
      By solving the Id equation of the respective transistor M1 and M3 we can get the equation(1) as:                                                     
   ![Equation will be:](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/Eq-1.jpeg)
 
   After putting the values of all typical mos parameters( V1 as Vtn=0.49) we can get the design constraint and M1 will be stronger than M3.
   ![equation-03](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/Eq-4.jpeg)
   

#### Write Operation:
In this state BL is forced to logic 0 and BLB & WL is connected to Vdd.  V1=Vdd and V2 = 0V.  Here to change the stored information, the node voltage V1 must be reduced below the thresold voltage of M2 so that M2 turns off first.
When V1=Vtn, the transistor M3 will be in linear region while M5 will be in saturation.
By solving the Id equation of M5 & M3 we can get the equation(2) as:

![Equation will be:](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/Eq-2.jpeg)

After putting the typical mos parameters values(V1=Vtn=0.49, Vtp=-0.66) in the equation 2, the equation will be
![equation 04](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/Eq-3.jpeg)



#### Pre-layout Simulation: 
 - DC_Analysis:
![VTC CURVE](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/vtc.png)
 - SNM_Hold:
![SNM HOLD](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/hold%20%282%29.png)
  - SNM_READ:
![SNM READ](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/Diagrams/read%20%282%29.png)
 
   
#### Acknowledgements:
-   Dr.Saroj Rout,Associate Professor,Silicon Institute Of Technology,Bhubaneswar
-   Mr.Santunu Sarangi,Assistant Professor,Silicon Institute Of Technology,Bhubaneswar
#### Contact Information:
- KrishnaMadhuChhanda Panda, Design Engineer,[Sevya Multimedia Technologies Pvt.Ltd](http://sevyamultimedia.com)
- [krishna.panda619@gmail.com](mailto:krishna.panda619@gmail.com) 
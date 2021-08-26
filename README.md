
### Design of 6T_SRAM.

#### Table of Contents:
 - [Introduction](#Introduction)
 - [Transistor Sizing](#Transistor_Sizing)
 - [Modes of Operations](#Modes)
    - [Read](#Read)
     - [Write](#Write)
  - [Pre-layout Simulation](#Prel-layout):
     - [DC](#DC) 
    - [SNM Hold](#SNM_HOLD)
    - [SNM Read](#SNM_READ)
    - [SNM Write](#SNM_WRITE)

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
   
      - [Schematic of 6T SRAM Cell](https://github.com/KrishnaMadhuchhanda/6T_-SRAM/blob/main/S_RAM/Screenshot%202021-08-26%20214325.png)
   

    
             
  

 
#### Acknowledgements
#### Contact Information
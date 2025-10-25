# RISC-V-Tapeout-Chip-program-Week-5
Continuing to the RISC V chip program tapeout journey, lts move to the week 5 which delas with the task of floorplanning and placement using OpenROAD tool.
### OpenROAD
OpenROAD is an open-source, fully automated RTL-to-GDSII flow for digital integrated circuit (IC) design. It supports synthesis, floorplanning, placement, clock tree synthesis, routing, and final layout generation. OpenROAD enables rapid design iterations, making it ideal for academic research and industry prototyping.

- Steps to install OpenROAD

     * Clone the OpenROAD repository

           git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts

<img width="1212" height="780" alt="Screenshot 2025-10-24 133913" src="https://github.com/user-attachments/assets/c0a91d80-79c1-4681-93ae-54fb6f841257" />

           cd OpenROAD-flow-scripts

    *  Run the setup script

           sudo ./setup.sh

<img width="1020" height="921" alt="Screenshot 2025-10-24 161443" src="https://github.com/user-attachments/assets/82ef8229-8902-4475-a795-b7f7ebffadcd" />

    * Build OpenROAD

           ./build_openroad.sh --local


    * Verify Installation

           source ./env.sh

           yosys -help  

           openroad -help

<img width="1855" height="960" alt="Screenshot 2025-10-24 161937" src="https://github.com/user-attachments/assets/1370f205-e381-4b75-a5b7-d9ab658e350e" />

    *  Run the OpenROAD flow
 
          cd flow

          make

    *  Launch the graphical user interface (GUI) to visualize the final layout
 
          make gui_final

<img width="1849" height="901" alt="Screenshot 2025-10-25 220543" src="https://github.com/user-attachments/assets/1f277971-7cc1-48cd-9052-f03bd45baf4a" />

- OpenROAD-flow-scripts             
  * docker           -> It has Docker based installation, run scripts and all saved here
  * docs             -> Documentation for OpenROAD or its flow scripts.  
  * flow             -> Files related to run RTL to GDS flow  
  * jenkins          -> It contains the regression test designed for each build update
  * tools            -> It contains all the required tools to run RTL to GDS flow
  * etc              -> Has the dependency installer script and other things
  * setup_env.sh     -> Its the source file to source all our OpenROAD rules to run the RTL to GDS flow

- flow           
   * design           -> It has built-in examples from RTL to GDS flow across different                                       technology nodes
   * makefile         -> The automated flow runs through makefile setup
   * platform         -> It has different technology note libraries, lef files, GDS etc 
   * tutorials        
   * util            
   * scripts       

<img width="775" height="224" alt="Screenshot 2025-10-25 100338" src="https://github.com/user-attachments/assets/bad2d47b-11db-4313-ac34-768d0de4159a" />

### Floorplanning
Floorplanning is the process of dividing the chip area and deciding the relative locations of major functional blocks (like ALU, memory, I/O, etc.) on the chip.
It involves the chip planning where the die size, macros and standard cells rows are consider without actually allocating the area. Its objective is to minimize the interconnect length and to avoid congestion.

In floorplanning the macros and the IO and power planning takes place.
- Specifies the die area and core area
     *  DIE_AREA: Specifies the die area dimensions as 0 0 1600 1600.
     *  CORE_AREA: Specifies the core area dimensions as 20 20 1590 1590.
- Run Floorplan
     make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk floorplan
  
- To view the Floorplan result
 make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_floorplan
<img width="648" height="466" alt="Screenshot 2025-10-25 202710" src="https://github.com/user-attachments/assets/be79fe1b-5128-428f-a357-0ca047040fd8" />
<img width="1017" height="996" alt="Screenshot 2025-10-25 202847" src="https://github.com/user-attachments/assets/45841a18-7a3b-4cde-8ddd-45a39592f707" />
<img width="461" height="357" alt="Screenshot 2025-10-25 203740" src="https://github.com/user-attachments/assets/bc2126dd-99b6-4955-9ef7-8bbe8fffddae" />
<img width="1488" height="920" alt="Screenshot 2025-10-25 213429" src="https://github.com/user-attachments/assets/9d80948d-aa3c-4445-b655-50a4d5e97ca8" />
<img width="1513" height="922" alt="Screenshot 2025-10-25 213451" src="https://github.com/user-attachments/assets/7afb3bf6-7071-4acf-94b2-dce236c69aba" />

### Placement
Placement is the process of assigning exact physical locations to standard cells (logic gates, flip-flops, etc.) within the floorplanned blocks.

 PLACE_PINS_ARGS: Arguments for pin placement, excluding certain areas on the die:
        -exclude left:0-600
        -exclude left:1000-1600
        -exclude right:*
        -exclude top:*
        -exclude bottom:*

- Run Placement
     make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk place

- To view the Placement result
     make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_place
<img width="1286" height="944" alt="Screenshot 2025-10-25 214134" src="https://github.com/user-attachments/assets/c270488b-d30a-4f37-bfff-2379d5c1a1e3" />

![7dcbb0eb-3666-48e9-a8e6-0c5e7f77b90c](https://github.com/user-attachments/assets/0b847692-7c5a-4728-ae8d-364b3fcaea9c)

### Acknowledgement
I'm veryy grateful to VSD teamm for this RISC-V tapeout chip program.

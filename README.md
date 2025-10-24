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

### Floorplanning
Floorplanning is the process of dividing the chip area and deciding the relative locations of major functional blocks (like ALU, memory, I/O, etc.) on the chip.
It involves the chip planning where the die size, macros and standard cells rows are consider without actually allocating the area. Its objective is to minimize the interconnect length and to avoid congestion.

In floorplanning the macros and the IO and power planning takes place.

### Placement
Placement is the process of assigning exact physical locations to standard cells (logic gates, flip-flops, etc.) within the floorplanned blocks.

### Acknowledgement
I'm veryy grateful to VSD teamm for this RISC-V tapeout chip program.

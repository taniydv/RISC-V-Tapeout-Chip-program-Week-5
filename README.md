# RISC-V-Tapeout-Chip-program-Week-5
Continuing to the RISC V chip program tapeout journey, lts move to the week 5 which delas with the task of floorplanning and placement using OpenROAD tool.
### OpenROAD
OpenROAD is an open-source, fully automated RTL-to-GDSII flow for digital integrated circuit (IC) design. It supports synthesis, floorplanning, placement, clock tree synthesis, routing, and final layout generation. OpenROAD enables rapid design iterations, making it ideal for academic research and industry prototyping.

- Steps to install OpenROAD

     * Clone the OpenROAD repository

           git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
       
           cd OpenROAD-flow-scripts

    *  Run the setup script

           sudo ./setup.sh

    * Build OpenROAD

           ./build_openroad.sh --local

    * Verify Installation

           source ./env.sh

           yosys -help  

           openroad -help
   
    *  Run the OpenROAD flow
 
          cd flow

          make

    *  Launch the graphical user interface (GUI) to visualize the final layout
 
          make gui_final

### Acknowledgement
I'm veryy grateful to VSD teamm for this RISC V tapeout chip program.

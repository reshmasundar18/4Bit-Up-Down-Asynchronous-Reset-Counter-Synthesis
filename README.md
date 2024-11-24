# EXP-4: 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

• Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)
• Synthesis: Genus

### Step 1: Getting Started

• Synthesis requires three files as follows,
◦ Liberty Files (.lib)
◦ Verilog/VHDL Files (.v or .vhdl or .vhd)
◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii→ Sets Clock Rise and Fall time to 100ps.

iii → Sets Clock Uncertainty to 10ps.

iv → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.
• In the terminal, initialise the tools with the following commands if a new terminal is being
used.
◦ csh
◦ source /cadence/install/cshrc
• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.
• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
![Screenshot 2024-11-24 183727](https://github.com/user-attachments/assets/bdb02356-0fe1-4e8e-8357-f25425ec7dd8)

#### Area report:
![Screenshot 2024-11-24 183831](https://github.com/user-attachments/assets/6035bb14-6c4d-4279-8276-1ca809a1f64b)

#### Power Report:
![Screenshot 2024-11-24 183925](https://github.com/user-attachments/assets/00f20523-5933-44c2-81ef-b98193e2f1cd)

#### Timing Report: 
![Screenshot 2024-11-24 184206](https://github.com/user-attachments/assets/0b63481d-af33-4c3d-9c7b-0a3edbd2180a)

#### Result: 
The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.






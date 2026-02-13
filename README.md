Low Power FIFO – RTL to Physical Design Flow
----------
📌 Overview

This repository contains the complete RTL-to-Physical Design implementation of a parameterized FIFO architecture developed as part of a Physical Design mastering journey.
The project covers the full digital implementation flow:

RTL Design (SystemVerilog)

Functional Verification

Logic Synthesis (Cadence Genus)

Floorplanning & Placement

Clock Tree Synthesis (CTS)

Post-CTS OptimizationRouting

Setup & Hold Timing Analysis

Power and Area Evaluation

The design is optimized with awareness of switching activity and timing behavior in sequential-dominant architectures.
---------
🏗 Design Specifications

Parameterized FIFO (Configurable Depth & Data Width)
Pointer-based read/write logic
Full and Empty flag generation
Synchronous reset
Single clock architecture (or mention dual clock if applicable)
Target Frequency: 1 GHz (modify if different)
---------------------
📁 Repository Structure
Copy code

├── rtl/
│   └── fifo.sv
│
├── tb/
│   └── fifo_tb.sv
│
├── constraints/
│   └── fifo.sdc
│
├── scripts/
│   ├── synth.tcl
│   ├── floorplan.tcl
│   ├── cts.tcl
│   └── route.tcl
│
├── reports/
│   ├── timing_reports/
│   ├── power_reports/
│   └── area_reports/
│
└── README.md

-----------------

🔹 File Descriptions

📄 fifo.sv (RTL Source)
Contains the synthesizable SystemVerilog implementation of the FIFO.

Key components:
Write pointer logic
Read pointer logic
Full/Empty detection
Data memory array
Control logic
Design considerations:
Clean sequential boundaries
Minimal combinational depth
Reduced unnecessary toggling
Timing-aware structure

🧪 fifo_tb.sv (Testbench)
Functional verification environment for FIFO.

Features:
Clock generation
Reset sequencing
Write and read stimulus
Full and empty boundary testing
Waveform dumping (VCD/FSDB if enabled)

Purpose:
Verify correct data ordering
Validate flag behavior
Ensure no overflow/underflow errors

📐 fifo.sdc (Design Constraints)
Defines timing constraints for synthesis and implementation.
Typical constraints include:
Clock definition
Clock uncertainty
Input/output delays
False paths (if applicable)
Max transition / max capacitance constraints

Example sections:
create_clock
set_input_delay
set_output_delay
set_clock_uncertainty
--------
Purpose: Controls timing targets and ensures realistic analysis.

🛠 .tcl Scripts (Automation Flow)
These scripts automate the full implementation process.

fifo.tcl
Reads libraries
Reads RTL
Applies SDC
Elaborates design
Optimizes and generates netlist
Produces synthesis reports
Report generation
Purpose: Ensures reproducible, script-driven implementation.

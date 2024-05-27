# <h1 id="header-1">Day 1 -Inception of open-source EDA, OpenLANE and sky130 PDK</h1>	 
## <h1 id="header-1_1">How to talk to computers?</h1>
### <h1 id="header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</h1>
#### Difference between chip and package
>*The chip is the core component where the actual processing happens. The package is the external enclosure that facilitates the chip’s use in electronic systems.Chip is the brain of the operation, while the package is the body that allows the brain to function in a practical and durable manner within electronic devices.

![Screenshot (571)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/12a15dbd-84c8-4d19-9a47-e8db57caddaf)


>*Packages are much larger than the chip itself and come in various forms, such as Dual In-line Package (DIP), Quad Flat Package (QFP), Ball Grid Array (BGA), etc. They are designed to provide a standardized way to connect the chip to the rest of the electronic system.
>*the connections from package is fed to the chip by WIRE BOUND method which is none other than basic wired connection.

![Screenshot (570)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/171f8fc9-f8cb-40b2-8f25-c448d0c3e80a)


#### Components 
(1) **Pads:** Pads are used to connect the internal circuitry of the chip to external circuits.Pads are used to send the signal inside the chip.</br>
(2) **Core:** The core is the heart of the chip, where the main processing or operational functions are performed. It contains the functional elements of the chip, such as the CPU, memory cells, logic gates, etc.</br>
(3) **Die:** The die encompasses the entire functional circuit and serves as the foundational piece that is packaged to create a usable component for electronic devices.</br>

![Screenshot (573)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/f9eae00f-b6d5-47b7-b39e-a3e27669147a)


#### RISC-V SOC
>* It consist of SRAM,SOC,ADC,DAC,SPI these all are called foundry IP's.All devices depends upon foundry where all chips are fabricated using deposition and lithography techniques and so on.

**Foundary:**  Foundry refers to a company or facility that specializes in the fabrication of semiconductor devices. It turns designs into physical chips. This includes photolithography, doping, etching, deposition, and other steps necessary to build the intricate structures of transistors and circuits on a silicon wafer.</br>

**Difference between macros and Foundry IPs:** FOUNDRY IP's are Intellectual Properties whereas MACROS are repeatable digital logic blocks.</br>
<b>Macros: </b>Optimized for general use within digital designs and may be reused across different projects and technologies.</br>
<b>Foundry IPs:</b> Optimized for specific foundry processes, ensuring they meet the process specifications and performance criteria of the foundry.</br>

![Screenshot (575)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/864b1cb4-0d54-4da5-aab0-564478de52da)

### <h1 id="header-1_1_2">Introduction to RISC-V</h1>
<b> ABOUT RISC-V ARCHITECTURE </b>

>* RISC-V is an open, versatile instruction-set architecture supporting diverse implementations.</br>
RISC-V is the first widely accepted open-source RISC processor.</br>
It features a base integer ISA, optional extensions, 32/64-bit variants, IEEE-754 floating-point support, and facilitates experimentation with privileged architectures, hypervisors, and parallel computing.

#### Intruction Set Architecture
To implement a C program on a specific hardware layout.<br>
**Compilation to Assembly Language:** The C program is initially compiled into an assembly language program using the RISC-V ISA (Reduced Instruction Set Computing - V Instruction Set Architecture).
<br>

**Conversion to Machine Language:** The assembly language program is then converted into a machine language program, which is in binary (logic 0 and 1). This binary code is what the hardware of the computer understands.
<br>

**RTL Implementation:** After obtaining the machine language program, we need to implement the RISC-V specification using an RTL (Register-Transfer Level) hardware description language. For example, we can use picorv32, which is an open-source implementation of the RISC-V ISA.
<br>

**RTL to Layout Flow:** The RTL code is then processed through a standard PnR (Place and Route) flow, often referred to as RTL to GDSII (Graphic Data System II). This flow typically involves synthesis, placement, routing, and other steps to generate the physical layout of the chip.
<br>
![Screenshot (576)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/6cf92767-7918-4e38-b09e-4c906e03388d)

### <h1 id="header-1_1_3">From Software Applications to Hardware</h1>

To run an application software on hardware, several processes take place involving both system software and hardware interaction. Here's a detailed step-by-step explanation of the process:

#### Application Software to Hardware Execution Flow
>* **1.Application Software Entry:-** The application software, written in a high-level language (e.g., C, C++, VB, or Java), enters the system software layer.

>* **2.System Software Components:-** The major components of system software involved in this process are the Operating System (OS), Compiler, and Assembler.

>* **3.Operating System (OS) Role:-** The OS manages the execution of application software and outputs small functions written in high-level languages (C, C++, VB, Java).
These functions are then handed over to the respective compiler.

>* **4.Compiler's Job:-** The compiler translates the high-level language code into assembly language instructions.
The syntax and structure of these instructions vary depending on the hardware architecture (e.g., x86, ARM, RISC-V) on which the system is implemented.
The output is often an executable file (.exe) that contains the compiled instructions.


>* **5.Assembler's Role:-** The assembler takes the assembly language instructions and converts them into binary format, known as machine language.
This machine language program is a sequence of binary codes (0s and 1s) that the hardware can understand.

>* **6.Binary Code Execution:-** The binary code is fed into the hardware, where it is executed. The hardware performs specific functions based on the binary instructions it receives.

![Screenshot (577)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/c1dd5aa6-c5bb-4891-a8dc-986f89ef0026)

#### EXAMPLE
* Suppose we have a C function to stop a stopwatch. This function enters the system software layer.
* The OS outputs this C function, and the compiler converts it into assembly language instructions tailored for the RISC-V architecture.
* The assembler then translates these RISC-V assembly instructions into binary machine code.
* This binary code is loaded into the chip (hardware), where it controls the stopping of the stopwatch.

![Screenshot (578)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/84210e79-b69d-4a65-9181-17cdac3062aa)

>* **1.Instruction Set Architecture (ISA):-** Instructions act as an abstract interface between the high-level language (C, C++) and the hardware.
In this case, the RISC-V Instruction Set Architecture (ISA) defines the instructions that the RISC-V hardware understands.

>* **2.Hardware Description Language (HDL) and RTL:-** To implement the RISC-V specifications on hardware, an HDL (e.g., Verilog) is used at the Register-Transfer Level (RTL).
The RTL code describes the hardware behavior.
>* The RTL code is then synthesized into a gate-level netlist, which describes the actual logic gates and connections required to perform the specified functions.
This netlist is used to fabricate the chip, ensuring the hardware performs the intended functions based on the binary instructions it receives.

![Screenshot (579)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/326ad533-edd7-4f37-8cf1-fb646cd1cc0b)

## <h1 id="header-1_2">Soc design and OpenLANE</h1>
### <h1 id="header-1_2_1">Introduction to all components of open-source digital asic design</h1>

Designing an ASIC (Application-Specific Integrated Circuit) involves several critical steps and the use of various tools and components.They are as follows:-
* **1.RTL (Register-Transfer Level) IPs:-** RTL is a level of abstraction used in describing the behavior of a digital circuit. RTL IPs (Intellectual Properties) are pre-designed, reusable blocks of RTL code that perform specific functions (e.g., memory controllers, communication interfaces, processors).
Example: A picorv32 core, which is an RTL implementation of a RISC-V processor.

* **2.EDA tools:-** EDA tools are software tools used to design and verify electronic systems such as ICs. They include various types of tools for different stages of the design process like Design Entry Tools,simulation tools,synthesis tools.
* **3.PDK Data:-** PDK (Process Design Kit) is a set of files and documentation provided by a semiconductor foundry that describes the manufacturing process and contains the necessary data to design and fabricate chips using that process.
 It includes design rules, device models, standard cell libraries, IO libraries, and technology files.
<br>
![Screenshot (585)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/681c7f48-734e-40dd-9dc7-664db53a65ad)

<b>SkyWater 130nm PDK</b>
Google has collaborated with SkyWater Technology, a semiconductor foundry, to provide open-source PDKs.The SkyWater 130nm PDK is a part of this initiative, offering designers access to a mature, reliable process technology that balances performance, power, and cost.Example: Intel Pentium 4 Extreme Edition (P4EE) @ 3.46GHz
![Screenshot (586)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/70df4495-3fc2-44f3-a6c5-3c12a699e389)
### <h1 id="header-1_2_2"> Simplified RTL2GDS flow</h1>
The main objective of the ASIC Design Flow is to take the design from the RTL (Register Transfer Level) all the way to the GDSII, which is the format used for the final fabrication layout.<br>
The ASIC design flow is a complex and iterative process involving several stages, each critical to the successful creation of a functional integrated circuit (IC).
![Screenshot (587)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/de1f82c8-0361-4bf1-87b3-23ffa9ea80ef)
<b>1.SYNTHESIS</b>
* **Objective:** Convert the RTL code into a gate-level netlist.
* **Tools:** Use synthesis tools (e.g., Synopsys Design Compiler) to optimize the design for performance, area, and power.
* **Output:** A gate-level netlist that describes the logic gates and their interconnections.

![Screenshot (588)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/41535158-cac3-4e3a-b816-71eca7a968fe)
![Screenshot (589)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/1f9e8f3f-3f0a-43ef-ab54-c128b2d33776)

<b>2.Floor Planning</b>
* **Objective:** Organize the layout of the chip, determining the placement of macros, I/O pads, and standard cells.
Types:<br>
* **Macro Floorplanning:** Define dimensions and positions of large blocks (macros), as well as the routing paths.
* **Chip Floorplanning:** For full-chip implementation, considering power distribution, signal integrity, and clock distribution.

![Screenshot (591)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/73c3e60c-d072-4d3b-8419-2d614011a870)

<b>3.POWER PLANNING</b>
* **Objective:** Design the power distribution network to supply adequate power to all parts of the chip.
Steps:<br>
* **Construct Power Network:** Design power grids and straps to minimize resistance and ensure uniform power distribution.
* **Use Upper Metal Layers:** Thicker metal layers (e.g., M8) are used for power distribution to reduce resistance and improve reliability.

  ![Screenshot (590)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/3585f003-8021-4407-8c2a-b3104b7f2557)
  
<b>4.PLACEMENT</b>
* **Objective:** Position the standard cells on the chip to minimize interconnect delay and optimize performance.
Types:<br>
* **Global Placement:** Find an optimal approximate position for cells without concern for legal placement. Ensures cells are close to minimize interconnect lengths.
* **Detailed Placement:** Adjust the positions from global placement to ensure all cells are legally placed without overlaps.

  ![Screenshot (592)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/299e9b01-30ef-4535-b73a-e73ea8494644)
  
<b>5.Clock Tree Synthesis (CTS)</b>
* **Objective:** Distribute the clock signal uniformly across the chip to minimize clock skew (differences in clock arrival times at different components).
Steps:<br>
* Design a clock tree structure that ensures balanced and synchronized clock distribution.
* Minimize skew and optimize for power and timing.

  ![Screenshot (594)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/7e8b6be9-29c0-48a5-a95b-ef90c8801ed9)
  
<b>6.ROUTING</b>
* **Objective:** Connect all the placed cells according to the netlist.
Types:<br>
* **Global Routing:** Plan the general routes for connections, focusing on optimal pathfinding without detailed geometric considerations.
* **Detailed Routing:** Finalize the exact geometric paths for all connections, ensuring they adhere to design rules and manufacturing constraints.
* skywater PDK has 6 routing layers in which the lowest layer is called the local interconnect layer which is a Titanium Nitride layer the following 5 layers are all Aluminium layers.
![Screenshot (595)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/15a27333-1383-44cc-ac0f-fc292c618ece)

<b>7.SIGN OFF</b>
* **Objective:** Ensure the design meets all functional, timing, and manufacturing requirements before tape-out.
Steps:<br>
* **Design Rule Checking (DRC):** Verify that the layout adheres to the foundry's manufacturing rules.
* **Layout Versus Schematic (LVS):** Ensure the final layout matches the original gate-level netlist.
* **Static Timing Analysis (STA):** Confirm that all timing constraints are satisfied and that the circuit will run at the designated frequency.

### <h1 id="header-1_2_3">Introduction to OpenLANE and Strive chipsets</h1>
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.

<b>Strive SoC Family</b>
Strive is a family of open everything SoCs.
* Open PDKs, Open EDA, Open RTL
![Screenshot (599)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/67b2b4c5-b397-4085-9ce4-e3b21404eb30)

The main goal of OPENLANE is to produce a clean GDSII with no human intervation (no-human-in-the-loop).

* No LVS violations
* No DRC Violations
* No timing Violations
OPENLANE is tuned for skyWter130nm open PDK. It can be used to harden Macros and chips.
It has two modes of operation:-
* Autonomus : Tt is the push botton flow due to this push botton, we get final GDSII
* Interactive : In this we can run commands and steps one by one.
It has large number of design examples(43 designs with their best configurations).

### <h1 id="header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</h1>

OpenLANE provides a comprehensive ASIC design flow that includes various stages from design entry to physical verification. Let's break down the detailed flow, incorporating each stage and how OpenLANE addresses them:
![Screenshot (598)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/56e7947c-e0a0-493b-9460-0824af666067)

The design exploration utility is also used for regression testing(CI).
<b>1. DFT (Design for Test)</b>
* **Objective:** Ensure the ASIC design is testable and can be reliably manufactured.
* **Scan Insertion:** Integrate scan chains into the design to facilitate testability.
* **Automatic Test Pattern Generation (ATPG):** Generate test patterns to detect and diagnose faults in the design.
* **Test Patterns Compaction:** Optimize test patterns for efficient testing and fault coverage.
* **Fault Coverage and Simulation:** Assess the effectiveness of test patterns in detecting faults and simulating various fault scenarios.

<b>2.Physical Implementation with OpenROAD</b>
* **Objective:** Transform the logical design into a physical layout.
* **Floor/Power Planning:** Organize the layout to optimize power distribution and signal routing.
* **End Decoupling Capacitors and Tap Cells Insertion:** Integrate decoupling capacitors and tap cells for stable power distribution and signal integrity.
* **Placements (Global and Detailed):** Place cells on the chip, optimizing for performance and minimizing wirelength.
* **Post Placement Optimization:** Refine placement to improve timing, area, and power.
* **Clock Tree Synthesis (CTS):** Generate a clock distribution network to ensure synchronous operation.
* **Routing (Global and Detailed):** Connect placed cells with wires, optimizing for signal integrity and manufacturability.
  
<b>Verification and Antenna Rules Violation Handling</b>
* **LCE (Yosys):** Formally confirm that design function remains unchanged after netlist modifications.
* **Antenna Rules Violation Handling:** Preventive approach by adding fake antenna diode cells and replacing them with real ones if violations occur during routing.
  
<b>3. Static Timing Analysis (STA)</b>
* **Objective:** Assess the timing performance of the design.
* **Interconnect RC Extraction (DEF2SPEF):** Extract resistance and capacitance information from the routed layout.
* **STA (OpenSTA):** Analyze timing constraints and identify violations, if any, to ensure timing closure.
  
<b>4. Physical Verification (DRC and LVS)</b>
* **Objective:** Ensure the design meets manufacturing requirements and is free from errors.
* **Design Rule Checking (DRC):** Verify layout against design rules to ensure manufacturability.
* **SPICE Extraction from Layout: Generate SPICE netlists from layout for detailed analysis.
* **Layout Versus Schematic (LVS): Compare layout against schematic to ensure functional correctness and electrical connectivity.

> OpenLANE provides a comprehensive ASIC design flow, addressing various stages from design entry to physical verification. By incorporating DFT techniques, physical implementation with OpenROAD, verification, and static timing analysis, designers can ensure their designs meet functional, timing, and manufacturing requirements. Additionally, the handling of antenna rules violations and thorough physical verification further enhance the reliability and manufacturability of the ASIC design.

## <h1 id="header-1_3">(LAB WORK)Get familiar to open-source EDA tools</h1>
### <h1 id="header-1_3_1">OpenLANE Directory structure in detail</h1>
Now we will do lab work so to do this.First we have to create virtual machine in Linux environment.<br>
OpenLANE leverages the OpenROAD tools and other open-source projects to facilitate the entire design process.
* The working directory in OpenLANE is where all the files related to a specific ASIC design project are organized and managed.
* Here we are working on  openlane_working_dir directory.
* **libs.ref**: Provides references to standard cell libraries and other component libraries needed for digital design stages such as synthesis, placement, and routing.
* **libs.tech:** Contains technology-specific rules and parameters needed for ensuring that the design adheres to manufacturing process capabilities and limitations.
  
  ![SOC1](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/26bde538-b958-41eb-8563-92d1c1d63bf2)
  
> * Above snap shows that we are working on the Sky130_fd_sc_hd PDK in the pdks file (Process Design Kit) which is a specific variant of the SkyWater 130nm process technology, tailored for standard cell-based digital design. The "hd" in Sky130_fd_sc_hd stands for "High Density" ,"fd" is a foundry name (skyWater foundry)."sc" means standerd cell library files.

![SOC2](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/c141ff68-c683-4356-925d-c9bceda02bad)

> * Above figure shows the contents of  Sky130_fd_sc_hd

### <h1 id="header-1_3_2">Design Preparation Step</h1>
![SOC3](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/c987a44d-c626-44d0-9e6b-d8b7b9ed2a0a)
> * Above figure shows the contents of opelane directory.
> * Give the following command in openlane
```
./flow.tcl -interactive 
```
> * The ./flow.tcl -interactive command is used to launch the OpenLANE ASIC design flow in interactive mode.Interactive mode allows you to run the design flow step-by-step, giving you control over each stage of the process. This is particularly useful for debugging, learning, and fine-tuning the design flow according to specific needs.
This command will start OpenLANE in interactive mode, presenting you with an OpenLANE prompt.
![soc21](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/93cf8ae3-3912-4e77-9b85-144abd748d48)


Now, If we are go into the design folder in openlane, there are nearly 30-40 designs are already built. Out of them we can open any of the design. for example, here we are opening the picorv32a.v design.
![SOC4](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/613842e1-e056-43c4-84fb-36a094283f9d)

<b> Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.</b>
> *The PicoRV32 is a minimalistic RISC-V CPU core, designed by Clifford Wolf. It is particularly suitable for use in FPGAs and ASICs due to its small size and configurability. The "picorv32a" variant refers to an area-optimized version of the PicoRV32 core. Here's an overview of the PicoRV32a design and its contents:

![SOC5](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/c8844d7a-9cb2-490a-9cdd-48b8f0e3a084)

It contains 3 files:-<br>
* **"src"**- It is where verilog files for our rtl netlist exists.src contains picorv32.v which is the  main Verilog file containing the RTL description of the PicoRV32 CPU core.

* **config.tcl**- Configuration files allow for the customization of the CPU core, enabling or disabling certain features to optimize for area, speed, or power consumption.
![SOC6](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/05a1a47f-6411-4f78-93e7-b196908c85d2)
 > The above figure shows the configuration of picorv32,showing design name ,clock period as 5.00,clock port etc.

Now In openlane, we are going to run the synthesis, but before synthesis, we have to include packages and prepare design setup stage. for that command is:-
```
% package require openlane 0.9
% prep -designs picorv32a
```
![SOC7](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/77cab21f-c749-45d3-b8d2-8e6075d9ecc2)
> The preparation is completed.In this lib.ref and lib.tech got merged.

### <h1 id="header-1_3_3">Review files after design prep and run synthesis</h1>
After completing the preparation, in the picorv32a file, the run directory is created. Inside the folder, Today's date is created. so in this directory some folders are available which is required for openlane.<br>
![WhatsApp Image 2024-05-26 at 00 30 52_f74483d6](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/0ef8ea07-7be8-4034-8701-587adc093dc0)

In the temp file, merged.lef file is available which was created in preparation time. if we open this merged.lef file, we get all the wire or layer level and cell level information.
![soc8](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/c21eab0f-82c3-4f1d-84f8-dad537017229)
The result directory is empty because  we have not run anything and in the report folder all the folders are there about synthesis, placement, floorplanning,cts,routing,magic,lvs which are still empty.
![WhatsApp Image 2024-05-26 at 00 32 34_b7e8fe89](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/bd167790-fb7b-4b9c-98b3-6ef8cc8f483e)
> Runs folder contains config.tcl which shows the parameters which are there in runs.When we make some changes in the original configuration and then we run, for example if we make a change in core utilization in the floorplanning and then we run the floorplanning, at this time in the config.tcl file, the core utility will change and by cross checking it ,we can check that the modification is reflected in the execution or not.

![WhatsApp Image 2024-05-26 at 00 32 53_4b0fb7ed](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/a048e2f6-a504-4ed6-9e5a-0c30238f2dae)
Now to do the Yosys synthesis:-
```
run_synthesis
```
![WhatsApp Image 2024-05-26 at 00 33 11_12df3949](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/858e28ff-517d-426a-9c24-0003bf9a3a4a)
The above figure shows the successfull synthesis.

### <h1 id="header-1_3_5">Steps to characterize synthesis results</h1>
* Now since the sysnthesis is done so now synthesis folder will contain files.
* The synthesis step, converts RTL code into a gate-level netlist.
  ![WhatsApp Image 2024-05-26 at 00 33 31_174b9712](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/9c45893e-2340-4106-ad01-5b54806dcb9f)
  
> Above figure the shows the synthesis of chip and its area too.

#### (Task-1) Calculation of the flop ratio.
.
```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ DFF's = Flop\ Ratio * 100
```
![WhatsApp Image 2024-05-26 at 00 33 47_258b9822](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/16aa1709-fad9-4f98-86a9-89ad4dde12a6)

> Here we have 14876 total number of cells and 1613 D flip-flops.
```math
Flop\ Ratio = \frac{1613}{14876} = 0.108429685
```
```math
Percentage\ of\ DFF's = 0.108429685 * 100 = 10.84296854\ \%
```
Lets now see the results which have now synthesised netlist which is picorv32a.synthesis.v.
![WhatsApp Image 2024-05-26 at 00 34 15_b02f7b52](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/3c48102c-8f75-4179-9f6a-70be07f00ee2)

We also have synthesis yosys report generated as yosys_4.stat.rpt
![WhatsApp Image 2024-05-26 at 00 34 45_9050dc83](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/d29f3030-686e-456e-aa7e-2198d46baf06)
![WhatsApp Image 2024-05-26 at 00 35 00_a136de19](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/fce5eb4a-edc8-45f4-812f-c59583998c20)

Similliary we can also check STA report as prelayout report generated as 2-opensta_min_max.rpt
![WhatsApp Image 2024-05-26 at 00 35 22_04dab527](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/7cb20d4a-0c12-4851-8287-a37646000318)
![WhatsApp Image 2024-05-26 at 00 35 44_cb325eb8](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/85c2b019-ec0e-44e9-9332-01aae66d1537)

# <h2 id="header-2">Day 2 - Good floor planning considerations</h2>	 
## <h2 id="header-2_1">Chip Floor planning consideration</h2>
### <h2 id="header-2_1_1">Utilization factor and aspect ratio</h2>
In  order to define width and height of core and die we take example of a simple netlist.Netlist is basically connectivities.The dimensions of the chip depends upon the dimensions of the logic gate.
![Screenshot (601)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/663797e9-06d9-4153-9135-371a8b379ca6)

we are interested in the dimensions of the standard cell so lets take a rough dimension.
![Screenshot (603)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/642fa305-060e-4b99-b1d0-846487b2ba07)

* **Die** which consists of core, is small semicondcutor material  specimen on which the fundamental circuit is fabricated.
* **Core** is the section of the chip where the fundamental logic of the design is placed.
 <b>UTILISATION FACTOR</b>
  
 ```
Utilization Factor = Area occupied by netlist / Total area of the core
```
Now, Let's try to place that particular logic inside the core. The netlist will occupy the whole area inside the core it means it utilizes the core 100%.The leftover area can be used to placed some additional cells like buffers, something else or for optimatisation.It can also be used for routing.
<b>ASPECT RATIO</b>
```
Aspect Ratio = Height /  width
```
If Aspect Ratio is 1 it signifies that chip is square shaped. If it is not 1 it means the chip is in rectangular shape.

### <h2 id="header-2_1_2"> Concept of pre-placed cells</h2>

>  preplaced cells are specific instances of cells or blocks that are manually positioned in the layout before the automatic placement of standard cells.
![Screenshot (605)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/78fa8d54-06d1-454d-88b5-5735b3ddede7)

Lets take a combinational logic which does some amount of function and assume its a huge circuit having some N Logic gates so let's divide it into some small numbers of gates. We will cut the whole circuit into two parts, and separate both of them into two blocks and both block will be implemented seperately.
![Screenshot (605)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/bcda07d6-9b85-4b9e-8aa3-89f50dd0c77d)

We can implement it once only but can use it multiple times. Similary there are other IP's also available for eg. Memory, Clock-gating cell, Comporator, MUX  all of these are part of the top level netlist.They recieve some signals and perform functions and deliver the outputs but the functionality of the cell is implemented only once. 
* The arrangement of these IP's in a chip is referd as **floorplanning**.
* These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called **"pre-placed cells"**. 
* These cells are placed in such a way that, the placement and routing tool do not touch the location of the cell.

### <h2 id="header-2_1_3">De-coupling capacitors</h2>
> Decoupling capacitors (decaps) play a critical role in ensuring stable and reliable operation of the integrated circuit. They are strategically placed around preplaced cells and throughout the chip to mitigate the effects of noise and voltage fluctuations.

<b>Function of Decoupling Capacitors</b>
* **1.Stabilizing Voltage Supply**
* When a gate, such as an AND gate, switches from 0 to 1 or 1 to 0, it requires a certain amount of switching current due to the capacitance associated with it. This capacitance must be fully charged to represent a logic '1' and completely discharged to represent a logic '0'.
* During switching, the instantaneous current demand causes a voltage drop across the resistive (Rdd) and inductive (Ldd) components of the power delivery network. This results in the supply voltage at the gate (Vdd') being lower than the intended Vdd, potentially causing the logic level to drop below the threshold required for a reliable logic '1'.
   ![Screenshot (606)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/ffb5ded2-49a2-4150-a65b-bdc18179b9ac)
> Above figure shows the problem of voltage drop in absence of decoupling capacitors.

* For example, if the ideal logic '1' is 1 volt, due to the voltage drop it gets less. This deviation can lead to unreliable operation if the voltage falls outside the noise margin.
 ![Screenshot (607)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5fd861c6-6952-4651-8fe6-897bf0e397af)

  * **2.Providing Instantaneous Current:**
  * Decoupling capacitors are placed in parallel with the circuit to provide the necessary instantaneous current when the circuit switches. This helps maintain the voltage at the required level.
![Screenshot (608)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/624c8870-9048-4b4f-aee7-e340ec58f274)

  * When the circuit switches, it draws current from the decoupling capacitor (Cd), which can supply the current quickly due to its low impedance. The main RL network replenishes the charge in Cd over time.
![Screenshot (609)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/cfa0ac00-7ed9-4501-bb92-8a02c4369a14)
> In the chip layout, decoupling capacitors are placed between Block A, Block B, and Block C to ensure a stable power supply. This strategic positioning provides the necessary instantaneous current during switching events, maintaining voltage stability. Consequently, local power distribution and communication within the chip are effectively managed.

### <h2 id="header-2_1_4">Power planning</h2>
<b>Problem:</b>

* Consider a local circuit as a black box that can be replicated multiple times, with logic present at its boundaries. The current demand problem is resolved using decoupling capacitors. However, a new problem arises when a signal is sent from a driver to a load, transitioning from logic 0 to logic 1. It is essential to maintain the integrity of this signal along the entire path so that the load receives it correctly.
![Screenshot (610)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/b413529b-1c5c-4d19-b662-2fec4ca14313)

* Assume a 16-bit bus that needs to retain the same signal from the driver to the load, requiring sufficient power from the supply. Since it is not feasible to place decoupling capacitors everywhere, and the power supply is distant from the bus, a voltage drop inevitably occurs.
  ![Screenshot (611)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/dc1a9bcb-20a1-460d-9a66-982e0ffead67)

> When one line of the 16-bit bus is logic 1, the capacitor is charged to Vdd. Conversely, when the line is logic 0, the capacitor is discharged to ground. Consider this 16-bit bus connected to an inverter, causing all initially charged capacitors to discharge and vice-versa. The issue arises because all capacitors connect to a single ground, leading to a bump in the 'ground' tap point during discharging, known as Ground Bounce.

> If the bump size exceeds the noise margin level, it may enter an undefined state, making the signal unpredictable. Similarly, when capacitors charged to 0 volts must charge to V volts through a single Vdd tap point, it lowers the voltage at the Vdd tap point. As long as this voltage drop stays within the noise margin, it's acceptable, but if it enters an undefined region, it becomes unpredictable.

<b>Solution:</b>
* The problem of lowering supply voltage occurs because power is applied at only one point. The solution is to use multiple power supplies. This approach ensures that every block draws power from the nearest supply and dumps charge to the nearest ground, reducing voltage drops and ground bounces. It is mess power supply distribution.
  ![Screenshot (612)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/f9135d5b-4401-4cd2-9bfd-23735cbca55a)
  
So the final power planning with the mesh solution would look like:-
![Screenshot (613)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/00ab18bf-4bbf-4e24-b488-d7f3bc38517d)

### <h2 id="header-2_1_5">Pin placement and logical cell placement blockage</h2>
In chip design, pin placement and logical cell placement blockage are critical steps in the floor planning process.
<b>Example Design Overview</b>

> Consider a design with two circuits driven by different clocks, clk1 and clk2, with inputs Din1 and Din2 and outputs Dout1 and Dout2. There are also preplaced cells, BlockA and BlockB.
* BlockA receives inputs from Din1 and Din2.
* BlockB receives inputs from clk1 and clk2 and provides a clock output (clkOut).
This design has:
* 4 input ports: Din1, Din2, clk1, clk2
* 3 output ports: Dout1, Dout2, clkOut
Additionally, a more complex design with 6 input ports and 5 output ports is mentioned, demonstrating the need for careful pin placement and connectivity.
<b>Netlist and Core Integration</b>
> The connectivity information between the gates is coded in VHDL/Verilog, forming the netlist. This netlist is then placed within the core of the chip design. The area between the core and the die (the chip’s boundary) needs to be filled with pin information.
![Screenshot (616)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/ae96c131-4901-4af5-b047-50636823da1a)

<b>Pin Placement</b>
Pin placement is a collaborative effort:
* The frontend team designs the netlist and determines the connectivity of inputs and outputs.
* The backend team handles the physical pin placements on the chip.
Pins need to be placed strategically:
* Preplaced blocks (BlockA and BlockB) should be located near their respective input pins (Din1, Din2, clk1, clk2) for efficient signal routing.
* Clock pins (clk1, clk2, clkOut) are larger than other pins because they need to provide continuous signals with minimal resistance. Larger pins reduce resistance, ensuring faster and more reliable signal transmission.
  ![Screenshot (617)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5b77c186-a8dc-49d5-b928-40764769d56b)

<b>Logical Cell Placement Blockage</b>
> When placing pins, it’s essential to block certain areas to prevent routing and cell placements in these regions. This is known as logical cell placement blockage:

* The area around pin placements is blocked to ensure that routing and cell placement do not interfere with the signal paths.
* This blockage ensures that the signal paths for critical connections, like clock signals, remain unobstructed and efficient.
  ![Screenshot (618)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/4fb2b2eb-8cb8-4fca-9344-59b388e925b3)

### <h2 id="header-2_1_6">Steps to run floorplan using OpenLANE</h2>
Before run the floorplanning, we require some switches for the floorplanning. these we can get from the configuration from openlane.
* In order to do that we open README file of configuration folder,we will see the variables which are required at each step.
  by entering
  ```
  less README.md
  ```
  ![soc22](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/fbc6e285-096f-42f1-8b39-f4bf624ebb94)

* We can also see the synthesis ,library files,global variables,constraints set.These variables are switches
* We have FP_CORE_UTL set as 0.5 and FP_ASPECT_RATIO set as 1 by default,similiarly we have defined margined value,vertcal,horizontal etc.
  ![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/0bdb634b-8a9d-4976-8858-029c50fb5b69)
  Now we will see where are these switches set so if we will do
```
less floorplan.tcl
```
we can see the switches set in the floorplan.tcl.
* Here FP_IO_MODE says how we want our pin configuration to be around.0 means pin positioning is random but it is on equal distance.
  ![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/d0c3a636-5ad8-43e4-ba08-d9d49951b759)
In the OpenLANE lower priority is given to system default (floorplanning.tcl), the next priority is given to config.tcl and then priority is given to PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl).<br>

Now we see, with this settings how floorplan run.<br>
Give the following command
```
run_flooplan
```
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/3969cf04-3fc8-4fe4-923f-a7f04dd2f6ca)

### <h2 id="header-2_1_7">Review floorplan files and steps to view floorplan</h2>
In the run folder, we can see the config.tcl file. this file contains all the configuration that are taken by the flow. if we open the config.tcl file, then we can see that which are the parameters are accepted in the current flow.
The runs folder will contain the latest folder by today's date so let's open config.tcl of runs 
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/8d7771cb-f27a-4b7d-9305-bfb2841ce222)
> The latest runs config.tcl shows utilisation factor as 35 whereas in sky130A_sky130_fd_sc_hd_config.tcl of picorv32a we have utitisation factor as 35. so latest uf is overwritten by confif.tcl ,which is then overwritten by sky130A_sky130_fd_sc_hd_config.tcl.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/d8a11c03-63ae-432d-8936-03001e395d20)

To watch how floorplane looks, we have to go in the results. in the result, one def( design exchange formate) file is available.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/e7c59925-10ff-43f3-9637-0364d9e64ed1)
if we open this file, we can see all information about die area (0 0) (660685 671405), unit distance in micron (1000). 
* It means 1 micron means 1000 databased units. so 660685 and 671405 are databased units. and if we divide this by 1000 then we can get the dimensions of chips in micrometer.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/8209085a-1cd9-4f8b-977c-393ff704c9b4)

So, the width of chip is 660.685 micrometer and height of the chip is 671.405 micrometer.
#### TASK2
```
Area of the chip = width*height
Area = 660.685*671.405 square micronmeter.
Area = 443,587.212425  square micronmeter.
```
To see the actual layout after the flow, we have to open the magic tech file by adding the command
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def
```
 Magic file will open. <br>
 Now we can see the layout.
 
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5fc71de7-650e-4814-9eba-deefd5d03621)

### <h2 id="header-2_1_8">Review floorplan layout in Magic</h2>
To place the layout in center
* press S for selecting and then "V".
  ![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/7e6aaaa4-d4ee-4577-a91e-6d63b8b7262d)

In the layout we can see that, input output pins are at equal distance.

after selecting (To select object, first click on the object and then press 's' from keyboard. the object will hightlited. to zoom in the object, click on the object and then press 'z' and for zoom out press 'sft+z') one input pin, if we want to check the location or to know at on which layer it is available, we have to open tkcon window and type "what". it will shows all the details about that perticular pin.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/eb60644a-3e04-40a5-ada7-f272ffc3dfb6)
It shows that selected subcell is in the topmost section of picorv32a.

![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/51ea395e-95d5-495d-bee5-e66daca72a38)

> The pin at the end  is in the metal 3.similarly doing for the vertical pins, we find that this pin is at metal 2.

Along with the side rows,the Decap cells are arranged at the border of the side rows.<br>
here we can see that first standerd cells is for buffer 1. similarly other cells are for buffer 2, AND gate etc.<br>
* At the lower end standard cells are present.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/4277ecd5-07ea-4909-a590-5827a1356a97)




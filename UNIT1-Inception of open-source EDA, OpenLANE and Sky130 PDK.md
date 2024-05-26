# *NASSCOM-VSD SOC DESIGN AND PLANNING*
# Contents 
 <div class="unit1">
  <ul>
    <li><a href="#header-1">Day 1 - Inception of open-source EDA, OpenLANE and sky130 PDK</a></li>
	<ul>
        <li><a href="#header-1_1"> How to talk to computers</a></li>
		<ul>
			<li><a href="#header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_2">Introduction to RISC-V</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_3">From Software Applications to Hardware</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-1_2">Soc design and OpenLANE</a></li>
	      <ul>
			<li><a href="#header-1_2_1">Introduction to all components of open-source digital asic design</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_2"> Simplified RTL2GDS flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_3">Introduction to OpenLANE and Strive chipsets</a></li>
		</ul>
	      <ul>
			<li><a href="#header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-1_3">(LAB WORK)Get familiar to open-source EDA tools</a></li>
		<ul>
			<li><a href="#header-1_3_1">OpenLANE Directory structure in detail</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_2">Design Preparation Step</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_3">Review files after design prep and run synthesis</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_5">Steps to characterize synthesis results</a></li>
		</ul>
      </ul>
   </div>

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

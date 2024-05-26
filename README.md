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



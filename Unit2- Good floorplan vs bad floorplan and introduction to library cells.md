<div class="day2">
  <ul>
    <li><a href="#header-2">Day 2 - Good floor planning considerations</a></li>
	<ul>
        <li><a href="#header-2_1"> Chip Floor planning consideration</a></li>
		<ul>
			<li><a href="#header-2_1_1">Utilization factor and aspect ratio</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_2">Concept of pre-placed cells</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_3">De-coupling capacitors</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_1_4">Power planning</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_5">Pin placement and logical cell placement blockage</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_6">Steps to run floorplan using OpenLANE</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_7">Review floorplan files and steps to view floorplan/a></li>
		</ul>
	      <ul>
		      <li><a href="#header-2_1_8">Review floorplan layout in Magic</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-2_2">Library building and Placement</a></li>
	      <ul>
			<li><a href="#header-2_2_1">Netlist binding and initial place design</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_2">Optimize placement using estimated wire-length and capacitance</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_3">Final placement optimization</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_2_4">Need for libraries and characterization</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_5">Congestion aware placement using RePlAce</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-2_3">Cell design and characterization flows</a></li>
		 <ul>
			<li><a href="#header-2_3_1">Inputs for cell design flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_2">Circuit design steps</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_3">Layout design step</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_3_4">Typical characterization flow</a></li>
		</ul>
      </ul>
	  <ul>
        <li><a href="#header-2_4">General timing characterization parameters</a></li>
		   <ul>
			<li><a href="#header-2_4_1"> Timing threshold definitions</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_4_2">Propagation delay and transition time</a></li>
		</ul>
      </ul>
</div>

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

Advantage of doing this is we can reuse them multiple times after implimenting once only. Similary there are other IP's also available for eg. Memory, Clock-gating cell, Comporator, MUX  all of these are part of the top level netlist.They recieve some signals and perform functions and deliver the outputs but the functionality of the cell is implemented only once. 
The arrangement of these IP's in a chip is referd as **floorplanning**.
These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called **"pre-placed cells"**. 
These cells are placed in such a way that, the placement and routing tool do not touch the location of the cell.

### <h2 id="header-2_1_3">De-coupling capacitors</h2>

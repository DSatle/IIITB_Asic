
# IIITB_Asic_Divyam_Satle
This github repository maps the progress made in the ASIC design class under the guidance of Kunal Ghosh(Founder & CEO Inscopix,Inc). The repository progress as the project proceeds and utilizes the specific tool wherever its needed. Repository will also act as a reference to aspirants who aspire to work in semiconductor industry, all the tools used here are open source and all the necessary instructions are provided wherever its needed.
# Knowing the ASIC
ASIC stands for Application Specific Integrated Chips, as name suggests these chips are hard coded i.e. made for specific purpose and user can't change its functionality/program as incase of FPGA or Gate Array. These chips are are highly optimised when it comes to the three main aspects of a silicon chip i.e. small area, low power consumption & high performance. But all this comes at a cost hence ASIC chips are costly and using this is only viable when chips are manufactured in large number.
# Table of Contents
[Day 0](#day-0)

[Day 1](#day-1)

[Day 2](#day-2)

[Day 3](#day-3)

[Day 4](#day-4)

[Day 5](#day-5)

# Day_0_Software_Installation

Before moving towards the first step of learning the fundamental concepts ASIC design. This section deals with the installation of necessary tools required for the ASIC design.
## Software Installation


<details open>
<summary>
### Knowing Yosys
	</summary>
<br>
Yosys is a framework for Verilog RTL synthesis. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. Selected features and typical applications:

Process almost any synthesizable Verilog-2005 design
Converting Verilog to BLIF / EDIF/ BTOR / SMT-LIB / simple RTL Verilog / etc.
Built-in formal methods for checking properties and equivalence
Mapping to ASIC standard cell libraries (in Liberty File Format)
Mapping to Xilinx 7-Series and Lattice iCE40 and ECP5 FPGAs
Foundation and/or front-end for custom flows
Yosys can be adapted to perform any synthesis job by combining the existing passes (algorithms) using synthesis scripts and adding additional passes as needed by extending the Yosys C++ code base. Yosys also serves as backend for several tools that use formal methods to reason about designs, such as sby for SMT-solver-based formal property checking or mcy for evaluating the quality of testbenches with mutation coverage metrics. Yosys is free software licensed under the ISC license (a GPL compatible license that is similar in terms to the MIT license or the 2-clause BSD license).
</details>

**Steps to Install Yosys**
```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make 
$ sudo make install
```
![Yosys](https://github.com/DSatle/IIITB_Asic/assets/140998466/5aa618d6-63f5-433d-abd4-949d61e06621)


### Knowing Icarus Verilog  
ICARUS VERILOG
Icarus Verilog is an implementation of the Verilog hardware description language compiler that generates netlists in the desired format (EDIF). It supports the 1995, 2001 and 2005 versions of the standard, portions of SystemVerilog, and some extensions.Icarus Verilog is released under the GNU General Public License, Icarus Verilog is free software. Icarus is composed of a Verilog compiler (including a Verilog preprocessor) with support for plug-in backends, and a virtual machine that simulates the design.

**Steps to install Verilog**<br>
```
sudo apt-get install iverilog
```
![Verilog](https://github.com/DSatle/IIITB_Asic/assets/140998466/f89e230b-0cd2-4994-9d6c-18daabe59356)
### Knowing GTKWave
GTKWave is a fully featured GTK+ based wave viewer for Unix and Win32 which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing.

**Steps to install GTKWave**<br>
```
sudo apt update<br>
sudo apt install gtkwave
```
![Gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/4d457906-7133-4a3a-ab59-436683b3a1e7)

### Knowing NGSPICE
ngspice is the open source spice simulator for electric and electronic circuits comprising of JFETs, bipolar and MOS transistors, passive elements like R, L, or C, diodes, transmission lines and other devices, all interconnected in a netlist. Digital circuits are simulated as well, event driven and fast, from single gates to complex circuits. And you may enter the combination of both analog and digital as a mixed-signal circuit. ngspice offers a wealth of device models for active, passive, analog, and digital elements. Model parameters are provided by our collections, by the semiconductor device manufacturers, or from semiconductor foundries. The user can add their circuits as a netlist, and the output is one or more graphs of currents, voltages and other electrical quantities or is saved in a data file.

**Steps to install ngspice**

Download the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory and then follow the commands given below :
```
# Dependency for ngspice:
sudo apt-get install build-essential
sudo apt-get install libxaw7-dev

# ngspice installation:
tar -zxvf ngspice-40.tar.gz
cd ngspice-40
mkdir release
cd release
../configure  --with-x --with-readline=yes --disable-debug
make
sudo make install
```
### Knowing Openlane
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. It also provides a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII. Currently, it supports both A and B variants of the sky130 PDK, the C variant of the gf180mcu PDK, and instructions to add support for other (including proprietary) PDKs are documented. OpenLane abstracts the underlying open source utilities, and allows users to configure all their behavior with just a single configuration file.

**Steps to install Openlane**

Prior to the installation of the OpenLane install the dependencies and packages using the command shown below :
```
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
Docker Installation :
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 


# Check for installation
sudo docker run hello-world
```
### Knowing Magic
Magic is an electronic design automation (EDA) layout tool for very-large-scale integration (VLSI) integrated circuit (IC) originally written by John Ousterhout and his graduate students at UC Berkeley. Work began on the project in February 1983. The main difference between Magic and other VLSI design tools is its use of "corner-stitched" geometry, in which all layout is represented as a stack of planes, and each plane consists entirely of "tiles" (rectangles). Magic is primarily famous for writing the scripting interpreter language Tcl.

**Steps to install magic**
```
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
```
### Knowing OpenSTA
OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats such as Verilog netlist, Liberty library, SDC timing constraints, SDF delay annotation and SPEF parasitics. OpenSTA uses a TCL command interpreter to read the design, specify timing constraints and print timing reports.

**Steps to install OpenSTA**
Prior to the installation of the OpenSTA install the dependencies using the command shown below :
```
sudo apt-get install cmake clang gcc tcl swig bison flex
```
After installing the dependencies use the following command to install OpenSTA:
```
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
sudo make install
```

# Day_1 Introduction to Verilog design and Synthesis
## Terminologies 
### Simulator
A simulator is a software tool that can be used to check the functionality of a circuit design before it is implemented in hardware. It does this by simulating the behavior of the design in software, using a Hardware Description Language (HDL) such as Verilog or VHDL. RTL design is checked for adherence to the specifications by simulating the design. Simultor looks for the chnages on the input signals. Output of the simulator is a vcd file i.e. value change dump format.


### Design
Design is the actual verilog code or set of verilog codes which has the intended functionality to meeet with the required specifications. Design can be of different types like Behavioral, Structural, Data flow model. Here I have started with the behavioral design of a MUX.

#### Test Bench
Testbench is the setup to apply stimulus(test_vectors) to the design to check its functionality. Here I have uploaded the test bench for the for the MUX design.

![Test Bench](https://github.com/DSatle/IIITB_Asic/assets/140998466/6b56c270-7f7c-4d9d-b22c-135282fb41e8)


### Verilog based simulation flow
![Whole Process](https://github.com/DSatle/IIITB_Asic/assets/140998466/a8fd9846-658b-4893-b339-3daf3577d8d8)

## Github Cloning
### Steps to clone the github repository
First I made a new directory VSD, follow commands were used
```
mkdir VSD
cd VSD
mkdir VLSI
```
In VLSI directory I clonned the following github repository

https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

![Kunalg123](https://github.com/DSatle/IIITB_Asic/assets/140998466/bca70601-be94-42e8-8f73-be2c9c3d5a78)

Following commands were used to clone the github repository
```
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
````
Accessing the files 
After clonning the github repository here I accessed the content of the repository using the following commands
```
cd VSD
cd VLSI
cd sky130RTLDesignAndSynthesisWorkshop
cd verilog_files
```
![verilog files](https://github.com/DSatle/IIITB_Asic/assets/140998466/529fb477-4d1f-4aa6-89bf-4495946f29d7)

The verilog_model folder in \\wsl.localhost\Ubuntu\home\vsd\VLSI\sky130RTLDesignAndSynthesisWorkshop\my_lib. The verilog_files folder contains all the lab experiment verilog source files and corresponding testbench files needed to simulate the designs.

**Demostration of the Icarus Verilog and GTKWave**

To run the iverilog command the unbuntu should be in the same directory where verilog log files are presesnt this is done using the following commands
```
/home/vsd/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
Now simulation of RTL design and test bench is done using the following commands
```
iverilog good_mux.v tb_good_mux.v 
```
![Screenshot (8)](https://github.com/DSatle/IIITB_Asic/assets/140998466/935509e1-6606-42b3-b070-96d48354e835)

The above command will compile and check for the syntax errors in both the design and testbench. Upon compiling successfully it will generate an executable file a.out.

Execute the a.out using the command ./a.out , resulting in the generation of a tb_good_mux.vcd file that captures changes in the input and output values. This vcd file is given as the input to the GTKWave to view the wave form. In GTKWave drag and drop the required input and output signals to view the waveform. Since the simulation is done for long amount of time use the zoom to fit option to view the entire waveform.

Commands to execute to view the waveform :
```
gtkwave tb_good_mux.vcd
```

![Screenshot (7)](https://github.com/DSatle/IIITB_Asic/assets/140998466/22053a27-982f-4fb0-9b55-b29b9347fe43)

**Descrpition of Verilog Code**

The verilog code can be viewed using the following commands
```
gedit good_mux.v
```
The above code opens the verilog code for 2x1 MUX writen in behavioral pattern.

![Mux Design](https://github.com/DSatle/IIITB_Asic/assets/140998466/e6cfa22b-3539-464d-a3c8-52fde1575e02)

```
gedit tb_good_mux.v
```
The above code opens the verilog code for test bench of 2x1 MUX writen in behavioral pattern.

![MUX test bench](https://github.com/DSatle/IIITB_Asic/assets/140998466/3606496c-9185-41d2-86ad-cd2dd0666183)

**Process of Synthesis i.e RTL(Verilog code to Netlist)**

**Terminologies**

**Synthesis**- Synthesis is the process that converts RTL into a technology-specific gate-level netlist, optimized for a set of pre-defined constraints.

**Netlist**- Netlist is the schematic or circuit equivalent of the RTL code. Netlist can be of various type based on its representation. A netlist can have elements like MUX, multiplier, adder, etc or it can be a gate level netlist where the given RTL code is implemented using gates the netlist shows the interconnection between gates.
Library- Library is the collection of all the standard cells needed to implement the given RTL logic thriugh a circuit. It consists of gates with various configutations 2,3,4 inputs or with different delay times.

**Introduction to the synthesizer**

Synthesizer is a tool used to convert the RTL from the netlist. Yosys is one such open source synthesizer. Yosys is provided with both the design and its corresponding .lib file, and its task is to generate the netlist. The netlist generated is a depiction of the input design provided to Yosys, contructed using the standard cells available in the .lib file. To validate the synthesis output, the netlist is verified in a manner analogous to how the RTL design is verified. This involves using the same testbench and stimulus set to confirm that the outcomes obtained from the netlist correspond to those acquired when using the RTL design. 

**Generating the netlist**

Here our synthesizer is Yosys, the following image shows the process and three command needed to generate the netlist using yosys

![Screenshot (12)](https://github.com/DSatle/IIITB_Asic/assets/140998466/1da95471-c269-4197-83fe-b23e0b6346a5)

The below picture describes the RTL design along with the netlist corresponding to it.

![Screenshot (16)](https://github.com/DSatle/IIITB_Asic/assets/140998466/ef1e161a-3ab0-4e5b-a885-f03337b3a4ea)


**Verifying the netlist**

Netlist verification is done to cross check whether the given netlist performs exactly in the same as the RTL design. The image shows the pictorial representation of verifying the netlist using the test bench.

![netlist_verification](https://github.com/DSatle/IIITB_Asic/assets/140998466/03daf290-81af-4b55-845a-413418911bd5)

**Need for slow gates in library**

**Setup Time**- The amount of time the data at the synchronous input must be stable before the active edge of the clock.

**Hold Time**- The amount of time the data at the synchronous input must be stable after the active edge of the clock.

![Setup and hold time](https://github.com/DSatle/IIITB_Asic/assets/140998466/da9e764a-aa58-4ee8-9b6b-872b7b609695)

Note- Both setup and hold time for the flipflops is specified in the librbary.

Invoking yosys
```
yosys
```
![Invoking Yosys](https://github.com/DSatle/IIITB_Asic/assets/140998466/8f3ac985-640b-4ef4-ae2f-b67c848ec92b)

Reading library

read_liberty /home/full directory where RTL code is present.

Reading Verilog code
read_verilog filename.v


Synthesize command 
```
synth -top filename
```
![Screenshot (19)](https://github.com/DSatle/IIITB_Asic/assets/140998466/9120c95a-c225-48da-83e4-27a8a8784576)

Abc command
```
abc_liberty -lib /home/file directory where library is present 
```
Show command
```
show
```

Note- In the coming we will see the 


![Setup and hold time](https://github.com/DSatle/IIITB_Asic/assets/140998466/5bd55f3f-5841-4b3b-bc76-5a19c047d900)

The below image explains why we need slower gates. In the image for proper functioning of the circuit data should reach DFFB well before(setup time) the next clock pulse arrives. And DFFB should hold this value for some amount of time (Hold time) so that it can be carry forward the value to next element of the circuit.

![Setup   Hold Time (2)](https://github.com/DSatle/IIITB_Asic/assets/140998466/38a6ba79-82c3-47b4-bdf2-dcfd878912b0)

Hence we need fast cells to meet the required performance and we need cells that work slow to meet HOLD.

**

## Day_2 Timing libs, hierarchial vs flat synthesis & efficient flop coding styles

**Introduction to timing.libs**

Library Name- Sky130

tt- Stands for typical process

025C- Temparature 

1V80- Indicates the voltage

Three important parameters

Process- Variations due to fabrication, due to human error every time it cannot be exactly made same

Voltage- Change in voltage results n change in behaviour of circuit.

Temperature- Semiconductors are highly sensitive to temparature.

Cells- Basic entity used to make a circuit like gates flipflops.

Command for getting library

![Command SS for getting library code](https://github.com/DSatle/IIITB_Asic/assets/140998466/b2779e85-b79f-4f25-a11f-2a356e741407)

Library details

![Lib img-1](https://github.com/DSatle/IIITB_Asic/assets/140998466/3dc45fe8-d031-4f7b-8461-fbf239921f2f)

![Lib img 2](https://github.com/DSatle/IIITB_Asic/assets/140998466/ecbe1e1f-4d23-4736-9bcd-1aae0b197762)


**Hierarchial vs Float synthesis**
File showing difference between and gates

![Screenshot (43)](https://github.com/DSatle/IIITB_Asic/assets/140998466/38507182-c6a5-4338-83ba-7e2c00f7f8dc)

Behavioral code of AND gate

![AND behavioral](https://github.com/DSatle/IIITB_Asic/assets/140998466/7f903ac5-ee3f-431e-99f3-cbe486f242ae)

Searching two input gate in library

![a211o search bar](https://github.com/DSatle/IIITB_Asic/assets/140998466/c07282e2-3ef7-4c7e-aa44-d615ad26da1b)

Searching three input gate in library


![a21110 search bar](https://github.com/DSatle/IIITB_Asic/assets/140998466/d50f8d5f-497f-4139-9297-7d68d33cdba1)

Verilog Code for multiple module 

![veri code mm](https://github.com/DSatle/IIITB_Asic/assets/140998466/655dcbd2-028a-4a12-ae10-ec56972b81c4)

Multiple module command for synthesis and netlist generation

![gedit multipl](https://github.com/DSatle/IIITB_Asic/assets/140998466/cb1fce1c-9ee1-4489-9222-f9ae5446a629)

![Invoking Yosys (2)](https://github.com/DSatle/IIITB_Asic/assets/140998466/5c473bf2-0a39-41c1-8778-0371c6eb0d2b)

![Syth](https://github.com/DSatle/IIITB_Asic/assets/140998466/59ba8959-6f8e-4cee-93e6-b257ce582fda)


Multiple module hierarchy 

![Multiple modules hier](https://github.com/DSatle/IIITB_Asic/assets/140998466/2930e3e1-f8d3-479d-892c-eb50b513e854)

Multiple module netlist 

![Multiple module net list](https://github.com/DSatle/IIITB_Asic/assets/140998466/0a8afab8-b4f2-4017-b86c-e65057f8c6ac)

Flattned Library file

![Flattened netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/9e824050-528e-41c7-b2c3-c1aafa7fb95a)

Flattned netlist

![Flattened netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/88611a0c-2e29-4bde-8129-9037a027a0e2)

Submodule AND gate

![Submodule AND gate](https://github.com/DSatle/IIITB_Asic/assets/140998466/f5bcc556-8ec3-466a-bf49-5699f3d45b3a)

**Various Flop Coding Styles and optimization**
Sync reset flipflop code

![sync dff](https://github.com/DSatle/IIITB_Asic/assets/140998466/eb408ac2-028d-4c61-90a1-31957128f822)

Simulation


![sync dff](https://github.com/DSatle/IIITB_Asic/assets/140998466/265f6f50-bbd7-4541-a156-f5e4f71c08cd)

Netlist 

![sync reset dff](https://github.com/DSatle/IIITB_Asic/assets/140998466/e8a63d53-4750-4853-ab08-ec4ab83ee63f)


Async reset flipflop code

![async reset](https://github.com/DSatle/IIITB_Asic/assets/140998466/975382c0-e708-412e-8775-78ad5e11459f)



Simulation

![gtkwave sync dff](https://github.com/DSatle/IIITB_Asic/assets/140998466/9fe90191-8576-4c65-8d72-c8b5e8173db1)

Netlist 

![dff async set](https://github.com/DSatle/IIITB_Asic/assets/140998466/99c5b49f-0611-467b-a603-9b45171afa0a)


Sync & Async flipflop code 

![Sync   async dff](https://github.com/DSatle/IIITB_Asic/assets/140998466/835d1285-2ce8-402c-b632-64082baa1f07)

**Interesting Optimisation**

Add image from phone here


## Day_3 Combinational and sequential optimizations

**Introduction to optimizations**
**Combinational Logic Optimisation**
* Seqeezing the logic to get the most optimised design
* Optimised Design is better interms of area & Power savings
There are two ways to do this
1. Constant Propagation
2. Boolean Logic optimisation
**Constant Propagation**
Below constant 0 helped to reduce the circuit hence termed as constant propagation
```
D3 ch1 I1
```
**Boolean Logic optimisation**
```
D3 ch1 I2
```

Example-1 
```
![opt_check](https://github.com/DSatle/IIITB_Asic/assets/140998466/be9fc551-6139-44af-af6a-6e3f5e822e9c)
```
Example-2
```
![opt_check2](https://github.com/DSatle/IIITB_Asic/assets/140998466/b3e10411-6050-4edf-85bb-e086c9615435)
```
Example-3
```
![opt_check3](https://github.com/DSatle/IIITB_Asic/assets/140998466/e89e0305-e0f9-4da7-a114-dec823bd2cb5)
```
Example-4
```
![ex-4](https://github.com/DSatle/IIITB_Asic/assets/140998466/8a8f74d9-5ac9-4ba3-bc89-4d32563e06c9)
```
Example-5 
Here there is multiple modules present so we will try to check whether those module are being used or not by using following commands:

```
yosys:read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys:read_verilog multiple_module_opt2.v
yosys:synth -top multiple_module_opt2
yosys:abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys:flatten
yosys:opt_clean -purge
yosys:show
```
```
module sub_module(input a , input b , output y);
	assign y = a & b;
endmodule

module multiple_module_opt2(input a , input b , input c , input d , output y);
	wire n1,n2,n3;
	sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
	sub_module U2 (.a(b), .b(c) , .y(n2));
	sub_module U3 (.a(n2), .b(d) , .y(n3));
	sub_module U4 (.a(n3), .b(n1) , .y(y));
endmodule
```
Before Flatten
![ex-5 bf](https://github.com/DSatle/IIITB_Asic/assets/140998466/0a78d50f-f911-48a9-b5db-2dc8486dea66)
After Flatten

![ex-5 af](https://github.com/DSatle/IIITB_Asic/assets/140998466/d40b7a04-5234-4466-84c4-d50c4ace62c8)

**Example -6
```
	module sub_module1(input a , input b , output y);
	 assign y = a & b;
	endmodule

	module sub_module2(input a , input b , output y);
	 assign y = a^b;
	endmodule

	module multiple_module_opt(input a , input b , input c , input d , output y);
	wire n1,n2,n3;
	sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
	sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
	sub_module2 U3 (.a(b), .b(d) , .y(n3));

	assign y = c | (b & n1); 
	endmodule
```
![ex-6 bf](https://github.com/DSatle/IIITB_Asic/assets/140998466/0391d03a-c647-412d-9ec3-6efdce739909)

![ex-6 af](https://github.com/DSatle/IIITB_Asic/assets/140998466/68105603-d788-4e05-a43b-1104f3cec255)


**Sequential Logic optimizations**
1. Sequential logic optimisations(basic)
2. Advanced
   2.1 State Optimisation
   2.2 Retiming
   2.3 Sequential Logic Clonning(Floor plan aware synthesis)
**State Optimisation**
Below figure show the concept of Sequential Constant
```
D3 ch1 I3
```
**Clonning**- Done when doing a physical aware synthesis

Below image shows concept of clonning 

```
D3 ch1 I4
```

When distance between A to B & A to C is very large & we have positive slack for A, we introduce more than one unit of A, this reduces the timing delay caused due to large distance.

**Retiming**

Below image shows the concept of retiming.
Assumption clock to Q delay & setup time zero. Effectively we will be able to clock at 200Mhz. After retiming is done circuit can be clocked at 250Mhz, making it faster.
```
D3 ch1 I4
```
Example-1 

![dff 1 netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/0b0c170b-a0c8-4abe-bfde-390ecbfac855)

![dff 1 no  of cells](https://github.com/DSatle/IIITB_Asic/assets/140998466/a5bb4995-7b33-44ee-a935-710e1391f466)

Example-2 

![dff 2 netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/fdf8b316-fdc3-49e1-bce0-22b248c6b2d1)

![dff 2 no  of cells](https://github.com/DSatle/IIITB_Asic/assets/140998466/e5d1f8f1-0cdf-40f2-ae6b-d3fcdff9bd96)

Example-3

![dff 3 no  of cells](https://github.com/DSatle/IIITB_Asic/assets/140998466/95f2a7a5-60f7-4aab-9355-aacd1694cee0)

![dff3 no  of cells](https://github.com/DSatle/IIITB_Asic/assets/140998466/dbb16953-4924-4bb4-a76a-acaa35171a14)

Example-4 

![dff ex-4 nl](https://github.com/DSatle/IIITB_Asic/assets/140998466/b84a1691-a178-4960-ac67-9b588dfcec61)

Example-5

![dff ex-5 nl](https://github.com/DSatle/IIITB_Asic/assets/140998466/555c151e-cbc3-42ff-a724-ec480df10c26)

**Sequential optimisation of unused output**
**Counter**

![netlist counter](https://github.com/DSatle/IIITB_Asic/assets/140998466/ceeb9b89-fc04-43d8-a54c-276e6a69f00a)

![IO Signals counter](https://github.com/DSatle/IIITB_Asic/assets/140998466/d9c911f0-b19d-4d58-b8a4-c8cec1c92310)

![counter cell counts](https://github.com/DSatle/IIITB_Asic/assets/140998466/86e2e474-6e2b-4171-8725-ec1dc2382ee7)

**Updated Counter**
![netlist counter2](https://github.com/DSatle/IIITB_Asic/assets/140998466/01452f60-b131-4b61-86d0-88c143c717b5)

![counter 2 IO signals](https://github.com/DSatle/IIITB_Asic/assets/140998466/cf694cce-de69-446d-b03f-e2efea7ff59e)

![counter2 cells](https://github.com/DSatle/IIITB_Asic/assets/140998466/61b640de-44c0-4cdd-823b-d460701ae7b9)

## Day_4 GLS, blocking and non-blocking and Synthesis-Simulation mismatch

**GLS, Synthesis-Simulation mismatch and blocking/nonblocking statements**

**What is GLS- Gate Level Simulation?**

GLS is generating the simulation output by running test bench with netlist file generated from synthesis as design under test. Netlist is logically same as RTL code, therefore, same test bench can be used for it.

**Why GLS?**

We perform this to verify logical correctness of the design after synthesizing it. Also ensuring the timing of the design is met.

Below picture gives an insight of the procedure. Here while using iverilog, we also include gate level verilog models to generate GLS simulation.

![GLS model timing conditon](https://github.com/DSatle/IIITB_Asic/assets/140998466/d9315151-6525-44eb-97b8-8fc3500a47c9)

**Synthesis Simulation Mismatch**

There are three main reasons for Synthesis Simulation Mismatch:

* Missing sensitivity list in always block
* Blocking vs Non-Blocking Assignments
* Non standard Verilog coding
  
**Missing sensitivity list in always block:**

If the consider - Example-2, we can see the only sel is mentioned in the sensitivity list. During the simulation, the waveforms will resemble a latched output but the simulation of netlist will not infer this as the synthesizer will only look at the statements with in the procedural block and not the sensitivity list.

As the synthesizer doen't look for sensitivity list and it looks only for the statements in procedural block, it infers correct circuit and if we simulate the netlist code, there will be a synthesis simulation mismatch.

To avoid the synthesis and simulation mismatch. It is very important to check the behaviour of the circuit first and then match it with the expected output seen in simulation and make sure there are no synthesis and simulation mismatches. This is why we use GLS.

**Blocking vs Non-Blocking Assignments:**

Blocking statements execute the statemetns in the order they are written inside the always block. Non-Blocking statements execute all the RHS and once always block is entered, the values are assigned to LHS. This will give mismatch as sometimes, improper use of blocking statements can create latches. Get to see at Example4


**Labs on GLS and Synthesis-Simulation Mismatch**

**Example-1** 

There is no mismatch in this example as the netlist simulation and rtl simulation waveform are similar only
```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
endmodule
```
**Simulation**

![GTKWave terniary mux](https://github.com/DSatle/IIITB_Asic/assets/140998466/f94a62c3-abf2-49b1-b1ff-f99d7e837794)

**Synthesis**

![terniary mux netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/b1261108-e52d-463b-8391-7ba769056aa0)

**Netlist Simulation**

![terniary netlist gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/220675f5-4c0b-479f-80f0-61ba1fc92300)

**Command for netlist verification**

![netlist verify code](https://github.com/DSatle/IIITB_Asic/assets/140998466/8bf7e134-5c63-4a5d-866a-c4b840663da3)


**Example-2**
```
module bad_mux (input i0 , input i1 , input sel , output reg y);
	always @ (sel)
	begin
		if(sel)
			y <= i1;
		else 
			y <= i0;
	end
endmodule
```
**Simulation**

![bad mux gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/c2b99647-766b-49ac-b323-13762a865927)

**Synthesis**

![bad mux netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/7f8ccaab-a5b9-4a50-a237-a4fd4bc2e655)

**Netlist Simulation**

![bbb](https://github.com/DSatle/IIITB_Asic/assets/140998466/e71ae49d-11ff-44d0-87ca-00888658a877)


**Mismatch**
Here the first image is showing mismatch because waveform was only changing only when select was changing where as in the second one it is corrected by the synthesizer.

![bad mux gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/2275d668-fd1c-4b6a-af76-63687817598b)

![bbb](https://github.com/DSatle/IIITB_Asic/assets/140998466/86a7de48-11d6-4a08-a165-581f4385fe2c)

**Command to get netlist**

![command to get bad bad with netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/5d4a2d1c-1d33-471c-86c8-709945ac0bd9)


**Example-3**
```
module good_mux (input i0 , input i1 , input sel , output reg y);
	always @ (*)
	begin
		if(sel)
			y <= i1;
		else 
			y <= i0;
	end
endmodule

```
**Simulation**

![good mux following](https://github.com/DSatle/IIITB_Asic/assets/140998466/035b0046-4c63-4cc8-87ca-83330a5fbc23)

**Synthesis**

![good mux following](https://github.com/DSatle/IIITB_Asic/assets/140998466/2b1be7cc-0e80-4714-9c8b-7c87891e5979)

**Netlist Simulation**

![netlist gm](https://github.com/DSatle/IIITB_Asic/assets/140998466/b05cb837-abf7-4204-863c-dceec8ab4484)


**Labs on synth-sim mismatch for blocking statement**
Here in the below example  the output is depending on the past value of x which is dependednt on a and b and it appears like a flop.
```
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
	begin
	d = x & c;
	x = a | b;
end
endmodule

```
```
D4 ch3 I1
```
**Simulation**

![gtkwave blocking caveat](https://github.com/DSatle/IIITB_Asic/assets/140998466/81cad32e-e80c-49aa-b0f2-cf3cc4c30c5a)

**Synthesis**

![netlist blocking caveat](https://github.com/DSatle/IIITB_Asic/assets/140998466/3914bdad-98b1-4275-b65e-2e3eda727f06)

**Cell Stats**

![cell stats blocking caveat](https://github.com/DSatle/IIITB_Asic/assets/140998466/683b4f11-89b5-4883-8882-7bb630b04b2f)

**Signal Info**

![signal info blocking caveat](https://github.com/DSatle/IIITB_Asic/assets/140998466/afb87746-4205-452d-84a7-0286f33fb3d4)

**Netlist Verification**

![mnmn](https://github.com/DSatle/IIITB_Asic/assets/140998466/b81d3524-416c-45f9-85cd-49fca4af29e2)



## Day_5 If,case, for loop and for generate
**If & Case constructs**

The construct if is mainly used to create priority logic. In a nested if else construct, the conditions are given priority from top to bottom. Only if the condition is satisfied, if statement is executed and the compiler comes out of the block. If condition fails, it checks for next condition and so on as shown below.
Syntx of If is shown below
```
if (<condition 1>)
begin
-----------
-----------
end
else if (<condition 2>)
begin
-----------
-----------
end
else if (<condition 3>)
.
.
.

```

**Dangers due to If**

If use a bad coding style i.e, using incomplete if else constructs will infer a latch. We definetly don't require an unwanted latch in a combinational circuit. When an incomplete construct is used, if all the conditions are failed, the input is latched to the output and hence we don't get desired output unless we need a latch.
The below image shows dangers with warning in red
```
D5 ch1 I1
```
**Case Construct**

In case construct, the execution checks for all the case statements and whichever satisfies the statement, that particular statement is executed.If there is no match, the default statement is executed. But here unlike if construct, the execution doesn't stop once statement is satisfied, but it continues further.

Below snippet show the syntax for case statement

```
case(statement)
  case1: begin
       --------
	 --------
	 end
 case2: begin
	     --------
	 --------
	 end
 default:
 endcase
```
Caveats in case occurs due to two primary reasons
1. Incomplete case
   The below image show the code and how a latch is formed in the case statement. Warning are shown in red colour.
   ```
   D5 ch1 I2
   ```
   Solution- Introducing a default in the code eliminates the problem of latch formation at hardware level.The snippet for which is shown below
   
2. Partial assignments
The below image shows the error occured due to partial assingment. Due to this hardware generates some random error. Example of this is discussed in further section.

```
D5 ch1 I3
```


**Lab incomplete if case**

**Example-1**

The below image shows the practical example where latch is formed due to incomplete if code used.

   ![incom if code](https://github.com/DSatle/IIITB_Asic/assets/140998466/269b8a30-08db-40d7-8d0b-c2df16ebbab4)

The below image show the image of latch at hardware level. Whenever io is low y is latching at some value.

![gtkwave incom if](https://github.com/DSatle/IIITB_Asic/assets/140998466/ff07651c-07b3-425c-9893-d609c613571f)

The below image show the latch used by the synthesizer to implement the circuit.

![cell stats incomp if](https://github.com/DSatle/IIITB_Asic/assets/140998466/2616ef12-9c4b-44d9-8296-fd5e7924c304)

The image shows presence of latch in the netlist



![incomp if netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/b5114974-df72-483f-8d61-c02f61aa0d07)

The above images shows what an incomplete if state does to the circuit at various levels

**Example-2**

The below code is equivalent to two 2:1 mux with i0 and i2 as select lines with i1 and i3 as inputs respectively. Here as well, the output is connected back to input in the form of a latch with an enable input of OR of i0 and i2.

![incom if2 code](https://github.com/DSatle/IIITB_Asic/assets/140998466/84ae9b77-b4de-442e-b211-3b4e907d51c2)

The below image shows when i1 and i2 are low the circuit will act as a latch.

![incom if2 gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/2b52e3fc-fd0d-4481-accb-b0ecc3d07640)

The below image shows that the synthesizer used a latch to implement the code at the hardware level.

![cell stats incomp if2](https://github.com/DSatle/IIITB_Asic/assets/140998466/10217c89-4c34-49f3-9f3e-9e77f050aa4d)

Below image shows latch present in the netlist.

![incomp if2 netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/7661c8d5-f12b-4a07-80c5-42206b392281)

**Lab-Incomplete overlapping case**

**Example-1**

This is an example of incomplete case where other two combinations 10 and 11 were not included. This will infer a latch for the multiplexer and connect i2 and i3 with the output.

Below is the code for the same.

![incomp cas1 code](https://github.com/DSatle/IIITB_Asic/assets/140998466/79a21569-4f9e-47f2-b667-81a97e6bfe6a)

Below show the gtkwave where latch can be observed for (1,0) & (1,1) it's forming the latch. This can be observed between 2ns to 4ns.

![incomp cas1 gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/d80e55c8-7bbc-410b-9678-36e9cfde58df)

The cell stats show the presence of latch in hardware implementation.

![cell stats cas1 incmo](https://github.com/DSatle/IIITB_Asic/assets/140998466/356ac6f4-fdf7-4b67-9bb3-a9d099a6ea63)

Presence of netlist is obserevd in the netlist as well.

![netlist incomp1](https://github.com/DSatle/IIITB_Asic/assets/140998466/4c2b6ab1-a7ae-4f46-937f-499827b08452)

**Example-2**
The below code is equivalent to two 2:1 mux with i0 and i2 as select lines with i1 and i3 as inputs respectively. Here as well, the output is connected back to input in the form of a latch with an enable input of OR of i0 and i2.

Code snippet is given below

![com case using default code](https://github.com/DSatle/IIITB_Asic/assets/140998466/dfbdcb1d-a748-4f1d-9106-e2dc289dfbb0)

Below image of GTKWave show the proper working of case statement by using default statement

![gtkwave comp gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/ea2a910f-8190-4f5c-8a5b-b7a608f596de)

Cell stats shows elimination of latch from hardware 

![cell stats comp case](https://github.com/DSatle/IIITB_Asic/assets/140998466/1a7a4a21-27e7-4235-9932-a1018b4902e7)

Same is reflected in the netlist as well.

![netlist comp cas](https://github.com/DSatle/IIITB_Asic/assets/140998466/e3fd9e22-c8f3-4e01-a230-02b8ca4ea70b)

**Example-3**

In the below example, y is present in all the case statements and it had particular outut for all cases. There no latch is inferred in case of y. When it comes to x, it is not assigned for the input 01, therefore a latch is inferred here.

Code snippet is given below

![code overlapping case](https://github.com/DSatle/IIITB_Asic/assets/140998466/f55388ef-fe12-44b7-83e6-9ca53480ee60)

GTKWave show output for both x and y.

![overlapping gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/8db55177-e8a0-4c28-a8fd-ce7666d1c7ca)

Cell stats shows inclusion of latch because of x.

![cell stats incomp 2 op](https://github.com/DSatle/IIITB_Asic/assets/140998466/0c6b804e-5baf-4665-b964-690374923264)

Netlist shows infered latch at output x.

![2 op case statement netlist](https://github.com/DSatle/IIITB_Asic/assets/140998466/8559648e-edde-40ec-93c0-6e1eb070ab67)

**Example-4 Bad Mux Contruct**

![bad case](https://github.com/DSatle/IIITB_Asic/assets/140998466/c86e7b1a-dd25-4ddd-851e-58199934dcb6)

GTKwave simulation

![nn](https://github.com/DSatle/IIITB_Asic/assets/140998466/9049fecf-440b-404b-8511-8afc3fc65e6f)

Cell stats

![cell stats for overlapping](https://github.com/DSatle/IIITB_Asic/assets/140998466/b2f6dc08-8e6c-4ebc-aaa3-571789c87317)

Netlist 

![nn n](https://github.com/DSatle/IIITB_Asic/assets/140998466/99503380-c0a7-4839-b573-011dff51340f)

**Netlist Simulation**

As we can see from the simulation wave form and difference in netlist waveform here the invalid case is getting fixed by the tool which we should avoid to do so in the code

![Capture](https://github.com/DSatle/IIITB_Asic/assets/140998466/d19c6a2b-92f1-4813-a1cc-c5c55894097d)

**For loop & For Generate**

* For loop is always used inside always block
* For loop used for evaluating expressions
* For loop is not used for instantiating Hard Ware multiple times

* Generate For loop is always used outside always block,
* Generate For loop is used when we need a code snippet multiple time i.e. used for instatiating Hard Ware.

  For loop can be used to generate larger circuits like 256:1 multiplexer or 1-256 demultiplexer where the coding style of smaller mux is not feesible and can have human errors since we would need to include huge number of combinations.

FOR Generate can be used to instantiate any number of sub modules with in a top module. For example, if we need a 32 bit ripple carry adder, instead of instantiating 32 full adders, we can write a generate for loop and connect the full adders appropriately.

**Lab- For and For Generate**
**Example-1- Mux using generate**

Code Snippet 

![Mux gene code](https://github.com/DSatle/IIITB_Asic/assets/140998466/dc38fb2a-7962-4845-8a05-4a8ac4792c87)

GTKwave output

![gtkwave mux gen code](https://github.com/DSatle/IIITB_Asic/assets/140998466/fad68d77-5d16-4182-91fb-44ab7b94e2ed)

Netlist 

![netlist mux gene](https://github.com/DSatle/IIITB_Asic/assets/140998466/2cc1d979-abac-456d-a0fb-4d6b657a83e0)

Netlist simulation

![netlist simulation mux generate](https://github.com/DSatle/IIITB_Asic/assets/140998466/e585e632-05f4-406a-ad53-c27715171d3a)

**Example-2-Demux using case & generate**
Code snippet

![combined code demux](https://github.com/DSatle/IIITB_Asic/assets/140998466/bda3a20a-c964-4b9f-ae5f-1ab57746e33e)

Demux Case RTL simulation

![demux case gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/9be052a6-0ba6-4ecc-baa1-db0c4cbd5afb)

Demux generate RTL simulation

![demux generate gtkwave](https://github.com/DSatle/IIITB_Asic/assets/140998466/244518fe-a757-495c-bc3c-47fb226e52d6)

Demux Case Netlist 

![netlist demux case](https://github.com/DSatle/IIITB_Asic/assets/140998466/0517bac4-653b-4359-91e7-2c0b251579b6)

Demux Generate Netlist

![netlist mux gene](https://github.com/DSatle/IIITB_Asic/assets/140998466/46a19316-06c9-46e9-981a-f0a53f8b2dbe)

Demux case Netlist Simulation

![case demux netlist simulation](https://github.com/DSatle/IIITB_Asic/assets/140998466/cc6af981-f752-44d2-a9b8-799ffc7d0274)

Demux generated Netlist simulation

![netlist simulation mux generate](https://github.com/DSatle/IIITB_Asic/assets/140998466/8ef4ca46-965a-46c4-aa2d-074654cfd3e8)

**Conclusion**- Whenever a big mux/demux is needed to be implemented "for" loop is very handy. Making larger mux using case statement is a tedious task, as the code length increases while this is not the case with for generate method.

**Example-4 Ripple Carry Adder**

In this Ripple carry adder example, unlike instantiating fulladder for 8 times, generate for loop is used to instantiate the fulladder for 7 times and only for first full adder, it is instantiated seperately. Using the same code, just by changing bus sizes and condition of for loop, we can design any required size of ripple carry adder.

Code snippet

![rca v](https://github.com/DSatle/IIITB_Asic/assets/140998466/8c8d74f5-16a3-4061-b478-5c0a351ce65e)

Simulation

![op gtkwave rca](https://github.com/DSatle/IIITB_Asic/assets/140998466/45b55412-0703-4298-beb0-32f72b6aefe0)

Synthesis 

Image add krna hai ask alwin for help

Netlist Simulation 

Image add krna hai ask alwin for help.







































   















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
### Knowing Yosys
Yosys is a framework for Verilog RTL synthesis. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. Selected features and typical applications:

Process almost any synthesizable Verilog-2005 design
Converting Verilog to BLIF / EDIF/ BTOR / SMT-LIB / simple RTL Verilog / etc.
Built-in formal methods for checking properties and equivalence
Mapping to ASIC standard cell libraries (in Liberty File Format)
Mapping to Xilinx 7-Series and Lattice iCE40 and ECP5 FPGAs
Foundation and/or front-end for custom flows
Yosys can be adapted to perform any synthesis job by combining the existing passes (algorithms) using synthesis scripts and adding additional passes as needed by extending the Yosys C++ code base. Yosys also serves as backend for several tools that use formal methods to reason about designs, such as sby for SMT-solver-based formal property checking or mcy for evaluating the quality of testbenches with mutation coverage metrics. Yosys is free software licensed under the ISC license (a GPL compatible license that is similar in terms to the MIT license or the 2-clause BSD license).

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

Note- Both setup and hold time for the flipflops is specified in the librbary.

![Setup and hold time](https://github.com/DSatle/IIITB_Asic/assets/140998466/5bd55f3f-5841-4b3b-bc76-5a19c047d900)

The below image explains why we need slower gates. In the image for proper functioning of the circuit data should reach DFFB well before(setup time) the next clock pulse arrives. And DFFB should hold this value for some amount of time (Hold time) so that it can be carry forward the value to next element of the circuit.

![Setup   Hold Time (2)](https://github.com/DSatle/IIITB_Asic/assets/140998466/38a6ba79-82c3-47b4-bdf2-dcfd878912b0)

Hence we need fast cells to meet the required performance and we need cells that work slow to meet HOLD.


## Day_2 Timing libs, hierarchial vs flat synthesis & efficient flop coding styles

**Introduction to timing.libs**







**Hierarchial vs Flaot synthesis**





**Various Flop Coding Styles and optimization**


## Day_3 Combinational and sequential optimizations

**Introduction to optimizations**




**Combinational Logic optimizations**


**Sequential Logic optimizations**


## Day_4 GLS, blocking and non-blocking and Synthesis-Simulation mismatch

**GLS, Synthesis-Simulation mismatch and blocking/nonblocking statements**

**Labs on GLS and Synthesis-Simulation Mismatch**

**Labs on synth-sim mismatch for blocking statement**

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
Example-1 
This is an example of incomplete case where other two combinations 10 and 11 were not included. This will infer a latch for the multiplexer and connect i2 and i3 with the output.

Below is the code for the same.

![incomp cas1 code](https://github.com/DSatle/IIITB_Asic/assets/140998466/79a21569-4f9e-47f2-b667-81a97e6bfe6a)








   














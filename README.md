# IIITB_Asic_Divyam_Satle
This github repository maps the progress made in the ASIC design class under the guidance of Kunal Ghosh(Founder & CEO Inscopix,Inc). The repository progress as the project proceeds and utilizes the specific tool wherever its needed. Repository will also act as a reference to aspirants who aspire to work in semiconductor industry, all the tools used here are open source and all the necessary instructions are provided wherever its needed.
# Knowing the ASIC
ASIC stands for Application Specific Integrated Chips, as name suggests these chips are hard coded i.e. made for specific purpose and user can't change its functionality/program as incase of FPGA or Gate Array. These chips are are highly optimised when it comes to the three main aspects of a silicon chip i.e. small area, low power consumption & high performance. But all this comes at a cost hence ASIC chips are costly and using this is only viable when chips are manufactured in large number.
# Table of Contents
[Day 0](#day-0)

[Day 1](#day-1)

[Day 2](#day-2)

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
***Steps to install magic***
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








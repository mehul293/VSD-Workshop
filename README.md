## Physical Design using Open-Source EDA Tools
### A 5 day workshop 
### CONTENTS:
1. *DAY 1 Study and review various components of RISC-V based picoSoC*
  * SKILL 1
    + Introduction to QFN-48 Package, chip,pads,core,die and IP's
  * SKILL 2
    + Introduction to RISC-V
    + From Software applications to hardware
  * SKILL 3
    + Pre-requisites and RISC-V, picorv32 and picoSoC review
    + Raven SoC 
  * SKILL 4
    + Installation of basic EDA tools
2. *DAY 2 Chip planning strategies and introduction to foundry library cells*
  * SKILL 1
    + utilization factor and aspect ration
    + concept of pre-placed cells
    + De-coupling capacitors
    + power planning
    + pin placement
    + pin arrangement
    + floorplanning
  * SKILL 2
    + netlist binding and initial place design
    + estimated wire length and capacitance
    + final placement optimization
    + libraries and characterization
  * SKILL 3
    + inouts for cell design
    + circuit design
    + layout design
    + characterization flow
  * SKILL 4
    + timing threshold
    + propagation delay and transition time

3. *DAY 3 Design and characterize one library cell using Magic Layout tool and ngspice*
  * SKILL 1- Labs for CMOS inverter ngspice simulation
    + Spice deck creation for CMOS inverter
    + Spice simulation lab for CMOS INverter
    + Switching threshold Vm
    + Static and Dynamic simulation of CMOS
  * SKILL 2- Art of layout using Euler's path plus stick diagram
    + Pre layout simulation of test circuit
    + Layout using only stick diagram
    + Euler's path for Fn-input gate reordering
    + Improved stick diagram for new input gate reordering
    + Abstract layout from stick diagram
  * SKILL 3- Lab for Magic and post-layout ngspice simulations
    + Derive actual dimension for Fn
    + Script to create layout in magic
    + Final layout and input/output labelling
    + Post layout ngspice simulation
  * SKILL 4- Inception of layout CMOD fabrication process
    + Create active region
    + Formation of n-well and p-well
    + Formation of gate
    + LDD formation
    + Source-drain formation
    + Local interconnect formation
    + Higher level metal formation

4. *DAY 4  Pre-layout timing analysis and importance of good clock tree*
  * SKILL 1- Timing modelling using delay table
    + Introduction to delay table
    + Delay table usage
  * SKILL 2- Timing analysis with ideal clock
    + Setup timing analysis and introduction to flip flop setup time
    + Introduction to clock jitter and uncertainity
  * SKILL 3- Clock tree synthesis and signal integrity
    + Clock tree routing and buffering using H-tree algorithm
    + crosstalk and net shielding
  * SKILL 4- Timing analysis with real clock
    + Setup timing analysing using real clock
    + Hold timing analysis using real clock

5. *DAY 5 Final steps for RTL2GDS*
  * SKILL 1- Routing and design rule check(DRC)
    + Introduction to maze routing
    + Lee's algoritm conclusion
    + Design rule check
    + Introduction to IEEE-1481--1999 SPEF format
    + SPEF representation of NET
    + Distributed resistance and capacitance in SPEF
    + SPEF header descrition
  * SKILL 2- PNR interactive flow tutorial
    + Few tips on PIN placement and floor planning chip
    + Placement and pre-route STA
    + Routing and post route STA
### TOOLS USED
#### The open source tools that are involved in this workshop are as follows

1. Yosys – for Synthesis, 
2. Graywolf – for Placement, 
3. Qrouter – for Routing, 
4. Netgen – for LVS, 
5. Magic – for Layout and Floorplanning, 
6. Qflow – RTL2GDS integration, 
7. OpenSTA & Opentimer -Pre-layout and Post-layout Static timing analysis

## LABS

### DAY1

#### Installation of basic EDA tools

1.Click on VSD IAT, Go to "Lab Instances". Then under "Links", click on the "link" icon. Click bottom left, System tools > LXTerminal. 

##### yosys is synthesis tool which is used to convert the rtl code into gate level netlist. To open the yosys tool, we use the command yosys.

![d1s4m3](https://user-images.githubusercontent.com/80052874/110325245-19d9da00-803d-11eb-862c-efb165e05588.PNG)

#### sta
##### “which” is command used to shows the loction/directory path of tool/folder.Linux which command is used to identify the location of a given executable that is executed when you type the executable name (command) in the terminal prompt. The command searches for the executable specified as an argument in the directories listed in the PATH environment variable.
which sta
![which sta](https://user-images.githubusercontent.com/80052874/110325370-44c42e00-803d-11eb-8bb7-c7884475d507.PNG)

*cd vsdflow
./vsdflow spi_slave_design_details.csv
ls -ltr outdir_spi_slave/*

##### The cd command, also known as chdir (change directory), is a command-line shell command used to change the current working directory in various operating systems. It can be used in shell scripts and batch files.cd vsdflow command is usedchange the directory to vsdflow folder../vsdflow spi_slave_design_details.csv is to initialize the design.The ls command lists the contents of a specified directory, excluding dotfiles. If no directory is specified then, by default, the contents of the current directory are listed. Listed files are sorted alphabetically.ls -ltr outdir_spi_slave | wc will show you the total 17 number of lines beacuse 1st line will give total number and the rest 16 are the number of flies.

![4](https://user-images.githubusercontent.com/80052874/110325628-91a80480-803d-11eb-923a-625de442c9ef.PNG)

*cd outdir_spi_slave
qflow display spi_slave*
It will open 2 windows "layout1" and "tkcon"

##### cd outdir_spi_slave command change the directory to outdir_spi_slave and the qflow display spi_slave command open and display the qflow manager where you do preference,synthesis,placement and so on.Qflow(complete tool chain) is a complete tool chain for synthesizing digital circuits starting from verilog source and ending in physical layout for a specific target fabrication process

![5](https://user-images.githubusercontent.com/80052874/110356737-90d49a00-8060-11eb-8f9f-2f73c30cac74.PNG)

##### 1st select the chip area and then type the command box in tkcon window.it shows the selected area in microns.
![6](https://user-images.githubusercontent.com/80052874/110357676-8c5cb100-8061-11eb-8a63-a3c7463e4fc7.PNG)


*cd
cd vsdflow
mkdir my_picorv32
cd my_picorv32
mkdir source synthesis layout
cp ~/vsdflow/verilog/picorv32.v source/.
qflow gui &*
![7](https://user-images.githubusercontent.com/80052874/110361369-eb242980-8065-11eb-8da9-43ccfb508871.PNG)

Select below options in gui

Technology = osu018

Verilog source file : picorv32.v

Verilog module : picorv32

![8](https://user-images.githubusercontent.com/80052874/110361518-26265d00-8066-11eb-81c3-d312948a96ef.PNG)

![9](https://user-images.githubusercontent.com/80052874/110362389-3985f800-8067-11eb-8f42-f6aaad3a6add.PNG)

![10](https://user-images.githubusercontent.com/80052874/110363681-dac17e00-8068-11eb-975e-0e5a46823440.PNG)

### DAY 2
#### Chip planning strategies and introduction to foundry library cells

![11](https://user-images.githubusercontent.com/80052874/110365646-473d7c80-806b-11eb-9b47-9278d9a34707.PNG)

*cd
cd vsdflow/my_picorv32
qflow display picorv32 &*
This will open layout and tkcon window In the layout window, select whole chip using below steps

![46](https://user-images.githubusercontent.com/80052874/110382791-65ae7280-8081-11eb-8b6a-e1b682d6bb42.PNG)

Take cursor to bottom left
Left mouse click
Take cursor to top right
Right mouse click
Press Shift+i
This will select the whole layout Now in tkcon window, type below command

box
![image](https://user-images.githubusercontent.com/80052871/110253596-36c8cb80-7fb1-11eb-946f-2964661d925a.png)


### DAY 3
####  Labs for CMOS inverter ngspice simulation
*cd
git clone https://github.com/kunalg123/ngspice_labs.git

![12](https://user-images.githubusercontent.com/80052874/110368977-bae18880-806f-11eb-98a5-d007fcce7686.PNG)

cd ngspice_labs
cat inv.spice*

![13](https://user-images.githubusercontent.com/80052874/110369107-e9f7fa00-806f-11eb-83b0-349011d80ac8.PNG)

*cd
cd ngspice_labs
ngspice inv.spice*
There will be terminal like below
ngspice 1 ->

![14](https://user-images.githubusercontent.com/80052874/110369207-13b12100-8070-11eb-9769-e2e665700b31.PNG)

On the above ngspice terminal, type below commands
*run
setplot dc1
plot out in*

![15](https://user-images.githubusercontent.com/80052874/110369380-5672f900-8070-11eb-9c4b-8ffbbdf2ae4a.PNG)

Go to labs, open terminal

Type below command

leafpad inv.spice

![16](https://user-images.githubusercontent.com/80052874/110370423-a69e8b00-8071-11eb-86bc-453e5870e867.PNG)

![15](https://user-images.githubusercontent.com/80052874/110370498-c0d86900-8071-11eb-9730-1f655ca610eb.PNG)

leafpad in_tran.spice

![17](https://user-images.githubusercontent.com/80052874/110370633-f1b89e00-8071-11eb-81a5-b17444564f47.PNG)

ngspice inv_tran.spice
ngspice 1 -> run
ngspice 1 -> setplot tran1
ngspice 1 -> plot out in

![18](https://user-images.githubusercontent.com/80052874/110371088-83281000-8072-11eb-8d77-2384f8cda570.PNG)

Rise delay= 114ps

![19](https://user-images.githubusercontent.com/80052874/110371450-02b5df00-8073-11eb-8880-d7439de02382.PNG)

#### Art of layout using Euler's path plus stick diagram
Go to labs, type below commands

*cd
cd ngspice_labs
ngspice fn_prelayout.spice
ngspice 1 -> run
ngspice 1 -> setplot tran1
ngspice 1 -> plot out 1.25*

![20](https://user-images.githubusercontent.com/80052874/110371664-4d375b80-8073-11eb-986d-ccb6f4f4b702.PNG)

![21](https://user-images.githubusercontent.com/80052874/110371826-82dc4480-8073-11eb-9689-0222a3106366.PNG)

Value of X0 at the intersection of horizontal blue line and middle rising waveform = Around 1.6e-09

![22](https://user-images.githubusercontent.com/80052874/110371928-a7382100-8073-11eb-853b-9f56838ef93a.PNG)

Value of X0 at the intersection of horizontal blue line and middle falling waveform = Around 2.2e-09

![23](https://user-images.githubusercontent.com/80052874/110372042-ce8eee00-8073-11eb-9246-52db74b4a2b0.PNG)

#### Lab for Magic and post-layout ngspice simulations

Go to labs, open terminal

Type below commands

*cd
cd ngspice_labs
magic -T min2.tech*
This will open magic layout window and tkcon window

![25](https://user-images.githubusercontent.com/80052874/110373518-97b9d780-8075-11eb-9109-aa0b7d37cac1.PNG)

8 nsubstratecontact and 6 polysilicon strips

Go to tkcon window and type below command
source draw_fn.tcl

![26](https://user-images.githubusercontent.com/80052874/110373666-c20b9500-8075-11eb-9a55-049e915bdc33.PNG)

area of the above design = 4489 unit^2

Go to labs, open terminal

Type below command

*cd
cd ngspice_labs
magic -T min2.tech fn_postlayout.mag &*

![27](https://user-images.githubusercontent.com/80052874/110373929-0eef6b80-8076-11eb-9826-4465f905c34a.PNG)

### DAY 4
####  Timing modelling using delay table

*cd
git clone https://github.com/kunalg123/ngspice_labs
cd ngspice_labs
cat inv_tran.spice*

 input rise slew and fall slew = 10ps, 10ps respectively

Go to Day 4 (When you start Day 4 labs, system will enable Day 2 labs for you. Click on Desktop icon)

Open terminal and Type below commands

*cd
cd ngspice_labs
cat inv_tran.spice

![28](https://user-images.githubusercontent.com/80052874/110374365-9dfc8380-8076-11eb-8eeb-3800bb06306b.PNG)

ngspice inv_tran.spice
load is 10fF and rise delay is ~126ps

![29](https://user-images.githubusercontent.com/80052874/110374691-f895df80-8076-11eb-9e70-fb4c2fd0dea4.PNG)

![30](https://user-images.githubusercontent.com/80052874/110374900-3f83d500-8077-11eb-87d7-d233c0733089.PNG)

Changing the load to 20f.

![31](https://user-images.githubusercontent.com/80052874/110375769-67276d00-8078-11eb-8cef-1b06193cbc9f.PNG)

![32](https://user-images.githubusercontent.com/80052874/110375920-94741b00-8078-11eb-9290-2700db5b3bc6.PNG)

#### Timing analysis with ideal clock

Go to labs Open below file using "leafpad" or "less" or "vim" - whichever you are comfortable with)

/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib
slew upper threshold pct fall = 80 

![33](https://user-images.githubusercontent.com/80052874/110377198-1f094a00-807a-11eb-846d-8ea343cffeba.PNG)

o/p threshold pct rise = 50%

![34](https://user-images.githubusercontent.com/80052874/110377315-4233f980-807a-11eb-9c37-88710fbac819.PNG)

variable 1 and variable 2

![35](https://user-images.githubusercontent.com/80052874/110377444-70193e00-807a-11eb-8911-7eef52148b71.PNG)

INVX1

![36](https://user-images.githubusercontent.com/80052874/110377599-9d65ec00-807a-11eb-8a81-904fe5509d52.PNG


Go to labs

Type below command

*cd
cd vsdflow/my_picorv32
leafpad picorv32.sdc*
Type below lines in the file picorv32.sdc file which you have just opened above

create_clock -name clk -period 2.5 -waveform {0 1.25} [get_ports clk]

![37](https://user-images.githubusercontent.com/80052874/110378067-2b41d700-807b-11eb-8da1-8a36a8a1d38e.PNG)

Save and close the above file

Now type below command

leafpad prelayout_sta.conf
Type below lines in prelayout_sta.conf file which you have just opened above

*read_liberty /usr/local/share/qflow/tech/osu018/osu018_stdcells.lib
read_verilog synthesis/picorv32.rtlnopwr.v
link_design picorv32
read_sdc picorv32.sdc
report_checks*

![38](https://user-images.githubusercontent.com/80052874/110378382-8c69aa80-807b-11eb-8464-8720a0be1518.PNG)

Now type below command

sta prelayout_sta.conf
SLACK value =-2.64

![39](https://user-images.githubusercontent.com/80052874/110379354-bc657d80-807c-11eb-8c4b-0a45f10cac9b.PNG)

data arrival time = 4.97ns

![40](https://user-images.githubusercontent.com/80052874/110379546-f6cf1a80-807c-11eb-9bee-54cfcdd7e409.PNG)

data required time =2.34ns

![41](https://user-images.githubusercontent.com/80052874/110379629-15351600-807d-11eb-9a92-305dd987fce7.PNG)

### DAY 5
#### PNR interactive flow tutorial

Open terminal

Type below commands

*cd
cd vsdflow/my_picorv32
qflow route picorv32
qflow sta picorv32
qflow backanno picorv32
leafpad log/sta.log*

![43](https://user-images.githubusercontent.com/80052874/110381638-bfae3880-807f-11eb-9dac-03d14266cb52.PNG)

![44](https://user-images.githubusercontent.com/80052874/110381722-df456100-807f-11eb-9e86-2993e13e8bdf.PNG)
pre-layout frequency = 314 MHz

![42](https://user-images.githubusercontent.com/80052874/110381862-16b40d80-8080-11eb-9a03-6321e969fe66.PNG)

log/post_sta.log
![45](https://user-images.githubusercontent.com/80052874/110381992-482cd900-8080-11eb-9fef-45e0130d74d0.PNG)

post-layout frequency = 297 MHz

## Acknowledgement

Kunal Ghosh -CO Founder VSD(VSD Corp.pvt.ltd)

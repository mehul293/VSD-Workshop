# VSD-physical-design
## Physical Design using Open-Source EDA Tools
### A 5 day course on physical designing using open source tools.
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

1.Click on VSD IAT, Go to "Lab Instances". Then under "Links", click on the "link" icon. Click bottom left, System tools > LXTerminal. 2.Now type the command "yosys". What do you see next?

![d1s4m3](https://user-images.githubusercontent.com/80052874/110325245-19d9da00-803d-11eb-862c-efb165e05588.PNG)

#### sta

which sta
![which sta](https://user-images.githubusercontent.com/80052874/110325370-44c42e00-803d-11eb-8bb7-c7884475d507.PNG)

*cd vsdflow
./vsdflow spi_slave_design_details.csv
ls -ltr outdir_spi_slave/*
![4](https://user-images.githubusercontent.com/80052874/110325628-91a80480-803d-11eb-923a-625de442c9ef.PNG)

*cd outdir_spi_slave
qflow display spi_slave*
It will open 2 windows "layout1" and "tkcon"
![5](https://user-images.githubusercontent.com/80052874/110356737-90d49a00-8060-11eb-8f9f-2f73c30cac74.PNG)

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

![11](https://user-images.githubusercontent.com/80052874/110365646-473d7c80-806b-11eb-9b47-9278d9a34707.PNG)

### DAY 2
#### Chip planning strategies and introduction to foundry library cells
![image](https://user-images.githubusercontent.com/80052871/110253632-55c75d80-7fb1-11eb-9664-5c160e72ccca.png)
![image](https://user-images.githubusercontent.com/80052871/110253635-595ae480-7fb1-11eb-942d-6fea51a386cc.png)
![image](https://user-images.githubusercontent.com/80052871/110253636-5bbd3e80-7fb1-11eb-8ad7-bd9cf63de461.png)

*cd
cd vsdflow/my_picorv32
qflow display picorv32 &*
This will open layout and tkcon window In the layout window, select whole chip using below steps
![image](https://user-images.githubusercontent.com/80052871/110253583-26b0ec00-7fb1-11eb-8061-259c41741687.png)

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
cd ngspice_labs
cat inv.spice*
![image](https://user-images.githubusercontent.com/80052871/110253698-c53d4d00-7fb1-11eb-8721-5c2f23537d20.png)

*cd
cd ngspice_labs
ngspice inv.spice*
There will be terminal like below
![image](https://user-images.githubusercontent.com/80052871/110253779-2402c680-7fb2-11eb-91aa-862412ed0eb5.png)
ngspice 1 ->
On the above ngspice terminal, type below commands

*run
setplot dc1
plot out in*
![image](https://user-images.githubusercontent.com/80052871/110253791-2e24c500-7fb2-11eb-950e-0c9dc167b312.png)

![image](https://user-images.githubusercontent.com/80052871/110253800-35e46980-7fb2-11eb-9b76-e512c2ef800e.png)
"x0" value lies between 1.0v-1.1v


Go to labs, open terminal

Type below command

leafpad inv.spice

![image](https://user-images.githubusercontent.com/80052871/110253847-6fb57000-7fb2-11eb-9631-c64cd0f7da3e.png)

![image](https://user-images.githubusercontent.com/80052871/110253937-d63a8e00-7fb2-11eb-92e4-f23993310296.png)

leafpad in_tran.spice
![image](https://user-images.githubusercontent.com/80052871/110253960-ece0e500-7fb2-11eb-94f6-cb7e2fbbae87.png)

ngspice inv_tran.spice
ngspice 1 -> run
ngspice 1 -> setplot tran1
ngspice 1 -> plot out in
![image](https://user-images.githubusercontent.com/80052871/110253978-01bd7880-7fb3-11eb-9a85-750021c087aa.png)
Rise delay= 76ps

#### Art of layout using Euler's path plus stick diagram
Go to labs, type below commands

*cd
cd ngspice_labs
ngspice fn_prelayout.spice
ngspice 1 -> run
ngspice 1 -> setplot tran1
ngspice 1 -> plot out 1.25*

![image](https://user-images.githubusercontent.com/80052871/110254047-6ed10e00-7fb3-11eb-8b0a-7b66663ae18d.png)
Value of X0 at the intersection of horizontal blue line and middle rising waveform = Around 1.6e-09

![image](https://user-images.githubusercontent.com/80052871/110254082-9a53f880-7fb3-11eb-83ab-5ea7fca05601.png)
Value of X0 at the intersection of horizontal blue line and middle falling waveform = Around 2.2e-09

#### Lab for Magic and post-layout ngspice simulations

Go to labs, open terminal

Type below commands

*cd
cd ngspice_labs
magic -T min2.tech*
This will open magic layout window and tkcon window
![image](https://user-images.githubusercontent.com/80052871/110254178-11898c80-7fb4-11eb-9877-deb68bcf5fa8.png)
8 nsubstratecontact and 6 polysilicon strips

Go to tkcon window and type below command

source draw_fn.tcl
![image](https://user-images.githubusercontent.com/80052871/110254163-f9b20880-7fb3-11eb-8f08-1067ec64e3f8.png)

![image](https://user-images.githubusercontent.com/80052871/110254205-2fef8800-7fb4-11eb-8308-f6e7f4689849.png)
area of the above design = 4489 unit^2

Go to labs, open terminal

Type below command

*cd
cd ngspice_labs
magic -T min2.tech fn_postlayout.mag &*

![image](https://user-images.githubusercontent.com/80052871/110254238-5e6d6300-7fb4-11eb-9e84-37d86df7fe68.png)

### DAY 4
####  Timing modelling using delay table

*cd
git clone https://github.com/kunalg123/ngspice_labs
cd ngspice_labs
cat inv_tran.spice*
![image](https://user-images.githubusercontent.com/80052871/110254534-9cb75200-7fb5-11eb-80a3-167808b73d25.png)
 input rise slew and fall slew = 10ps, 10ps respectively

Go to Day 4 (When you start Day 4 labs, system will enable Day 2 labs for you. Click on Desktop icon)

Open terminal and Type below commands

*cd
cd ngspice_labs
cat inv_tran.spice
ngspice inv_tran.spice*
![image](https://user-images.githubusercontent.com/80052871/110254396-fb300080-7fb4-11eb-9625-fa418abd2f25.png)

![image](https://user-images.githubusercontent.com/80052871/110254432-2286cd80-7fb5-11eb-8fd2-1e74b7d0ba78.png)
load is 10fF and rise delay is ~126ps

![image](https://user-images.githubusercontent.com/80052871/110254422-16027500-7fb5-11eb-885f-9a18ebe66b86.png)

![image](https://user-images.githubusercontent.com/80052871/110254465-3fbb9c00-7fb5-11eb-9a7b-6dc505d60735.png)
Changing the load to 20f.
![image](https://user-images.githubusercontent.com/80052871/110254735-5d3d3580-7fb6-11eb-9bd1-f81ae14a9eab.png)
![image](https://user-images.githubusercontent.com/80052871/110254741-66c69d80-7fb6-11eb-8c5d-abcf6f64568e.png)


#### Timing analysis with ideal clock

Go to labs Open below file using "leafpad" or "less" or "vim" - whichever you are comfortable with)

/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib

![image](https://user-images.githubusercontent.com/80052871/110254798-ad1bfc80-7fb6-11eb-88f2-bfa05d32ccb8.png)
slew upper threshold pct fall = 80 
![image](https://user-images.githubusercontent.com/80052871/110254838-e0f72200-7fb6-11eb-853e-13c7568578ad.png)
o/p threshold pct rise = 50%
![image](https://user-images.githubusercontent.com/80052871/110254870-0a17b280-7fb7-11eb-9e6b-e18d6deb9634.png)
variable 1 and variable 2
![image](https://user-images.githubusercontent.com/80052871/110254892-2a477180-7fb7-11eb-9c54-43fc91e9cfe0.png)
INVX1
![image](https://user-images.githubusercontent.com/80052871/110254901-33d0d980-7fb7-11eb-81ea-0954c4849b01.png)
Delay template 5x5


Go to labs

Type below command

*cd
cd vsdflow/my_picorv32
leafpad picorv32.sdc*
Type below lines in the file picorv32.sdc file which you have just opened above

create_clock -name clk -period 2.5 -waveform {0 1.25} [get_ports clk]
![image](https://user-images.githubusercontent.com/80052871/110254928-4ea34e00-7fb7-11eb-90d2-4c0797821c35.png)

Save and close the above file

Now type below command

leafpad prelayout_sta.conf
Type below lines in prelayout_sta.conf file which you have just opened above

*read_liberty /usr/local/share/qflow/tech/osu018/osu018_stdcells.lib
read_verilog synthesis/picorv32.rtlnopwr.v
link_design picorv32
read_sdc picorv32.sdc
report_checks*
![image](https://user-images.githubusercontent.com/80052871/110254940-59f67980-7fb7-11eb-8a03-c9da867c87ec.png)


Now type below command

sta prelayout_sta.conf
![image](https://user-images.githubusercontent.com/80052871/110254954-68449580-7fb7-11eb-8304-423980aeda15.png)
SLACK value =-0.56
![image](https://user-images.githubusercontent.com/80052871/110254959-6d094980-7fb7-11eb-8f41-f1742248047f.png)
data arrival time =2.9ns
![image](https://user-images.githubusercontent.com/80052871/110254960-709cd080-7fb7-11eb-8dbd-32e0eff94137.png)
data required time =2.3389ns


#### Timing analysis with real clock
Perform all steps in D4SK2 - MCQ11

You are now at below "sta" terminal

%
Type below command in above terminal

*set_propagated_clock [all_clocks]
report_checks*

![image](https://user-images.githubusercontent.com/80052871/110255131-4ac3fb80-7fb8-11eb-9608-c3433047b4ef.png)
SLACK value after clock propagation = around -0.68ns

![image](https://user-images.githubusercontent.com/80052871/110255286-ece3e380-7fb8-11eb-980c-967127118044.png)
launch clock network delay

![image](https://user-images.githubusercontent.com/80052871/110255319-10a72980-7fb9-11eb-84e7-b81a7b908a61.png)
capture clock network delay=0.56

Perform all steps in D4SK4 - MCQ3

Type below command

report_checks -path_delay min -digits 4

![image](https://user-images.githubusercontent.com/80052871/110255353-37656000-7fb9-11eb-8bfd-1f6ec16d0d8c.png)
![image](https://user-images.githubusercontent.com/80052871/110255356-3cc2aa80-7fb9-11eb-9f91-29f23c1be189.png)

library hold time and hold slack = -9.4ps and 222.5ps respectively


### DAY 5
#### PNR interactive flow tutorial
![image](https://user-images.githubusercontent.com/80052871/110255563-66c89c80-7fba-11eb-8367-678203f6a07e.png)

Go to Day 5 labs

Open terminal

Type below commands

*cd
cd vsdflow/my_picorv32
qflow route picorv32
qflow sta picorv32
qflow backanno picorv32
leafpad log/sta.log*

![image](https://user-images.githubusercontent.com/80052871/110255456-d427fd80-7fb9-11eb-8b61-6940477e68f2.png)
pre-layout frequency = 314 MHz

log/post_sta.log
![image](https://user-images.githubusercontent.com/80052871/110255490-12bdb800-7fba-11eb-8118-103a00d66d70.png)
post-layout frequency = 297 MHz

## Acknowledgement

Kunal Ghosh -CO Founder VSD(VSD Corp.pvt.ltd)

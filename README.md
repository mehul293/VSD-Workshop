# Physical design using open-source EDA Tools
## Contents:
1. Study and review various components of RISC-V based picoSoC
2. Chip planning strategies and introduction to foundry library cells
3. Design and characterize one library cell using Magic Layout tool and ngspice
4. Pre-layout timing analysis and importance of good clock tree
5. Final steps for RTL2GDS

### The open source tools that are involved in this workshop are as follows

![2](https://user-images.githubusercontent.com/80052874/110322494-38d66d00-8039-11eb-8a91-7415a413655b.PNG)


### DAY1

1.Click on VSD IAT, Go to "Lab Instances". Then under "Links", click on the "link" icon. Click bottom left, System tools > LXTerminal. 2.Now type the command "yosys". What do you see next?

![d1s4m3](https://user-images.githubusercontent.com/80052874/110321678-06784000-8038-11eb-9148-c26e8ebe139e.PNG)

### Invoked the flow using below git clone for vsdflow 
git clone https://github.com/kunalg123/vsdflow.git

*cd vsdflow
./vsdflow spi_slave_design_details.csv
ls -ltr outdir_spi_slave/*

Now type below command

ls -ltr outdir_spi_slave | wc


### D1SK4 - MCQ7

*cd outdir_spi_slave
qflow display spi_slave*
It will open 2 windows "layout1" and "tkcon"

On "tkcon" window, type "box".



### D1SK4 - MCQ8
*cd
cd vsdflow
mkdir my_picorv32
cd my_picorv32
mkdir source synthesis layout
cp ~/vsdflow/verilog/picorv32.v source/.
qflow gui &*

Select below options in gui

Technology = osu018

Verilog source file : picorv32.v

Verilog module : picorv32




### D2SK4 - MCQ5
*cd
cd vsdflow/my_picorv32
qflow display picorv32 &*
This will open layout and tkcon window In the layout window, select whole chip using below steps

Take cursor to bottom left
Left mouse click
Take cursor to top right
Right mouse click
Press Shift+i
This will select the whole layout Now in tkcon window, type below command

box



### D3SK1 - MCQ5,6,7
*cd
git clone https://github.com/kunalg123/ngspice_labs.git
cd ngspice_labs
cat inv.spice*


### D3SK1 - MCQ8

*cd
cd ngspice_labs
ngspice inv.spice*
There will be terminal like below

ngspice 1 ->
On the above ngspice terminal, type below commands

*run
setplot dc1
plot out in*




### D3SK1 - MCQ10
Go to labs, open terminal

Type below command

leafpad inv.spice




### D3SK2 - MCQ1
Go to labs, type below commands

*cd
cd ngspice_labs
ngspice fn_prelayout.spice
ngspice 1 -> run
ngspice 1 -> setplot tran1
ngspice 1 -> plot out 1.25*




### D3SK3 - MCQ3

Go to labs, open terminal

Type below commands

*cd
cd ngspice_labs
magic -T min2.tech*
This will open magic layout window and tkcon window

Go to tkcon window and type below command

source draw_fn.tcl




### D3SK3 - MCQ4
Go to labs, open terminal

Type below command

*cd
cd ngspice_labs
magic -T min2.tech fn_postlayout.mag &*



### D4SK1 - MCQ6

*cd
git clone https://github.com/kunalg123/ngspice_labs
cd ngspice_labs
cat inv_tran.spice*


### D4SK1 - MCQ7
Go to Day 4 (When you start Day 4 labs, system will enable Day 2 labs for you. Click on Desktop icon)

Open terminal and Type below commands

*cd
cd ngspice_labs
cat inv_tran.spice
ngspice inv_tran.spice*



### D4SK2 - MCQ6

Go to labs Open below file using "leafpad" or "less" or "vim" - whichever you are comfortable with)

/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib





### D4SK2 - MCQ11
Go to labs

Type below command

*cd
cd vsdflow/my_picorv32
leafpad picorv32.sdc*
Type below lines in the file picorv32.sdc file which you have just opened above

create_clock -name clk -period 2.5 -waveform {0 1.25} [get_ports clk]
Save and close the above file

Now type below command

leafpad prelayout_sta.conf
Type below lines in prelayout_sta.conf file which you have just opened above

*read_liberty /usr/local/share/qflow/tech/osu018/osu018_stdcells.lib
read_verilog synthesis/picorv32.rtlnopwr.v
link_design picorv32
read_sdc picorv32.sdc
report_checks*


Now type below command

sta prelayout_sta.conf


### D4SK4 - MCQ2
Perform all steps in D4SK2 - MCQ11

You are now at below "sta" terminal

%
Type below command in above terminal

*set_propagated_clock [all_clocks]
report_checks*




### D4SK4 - MCQ5
Perform all steps in D4SK4 - MCQ3

Type below command

report_checks -path_delay min -digits 4




### D5SK2 - MCQ1
Go to Day 5 labs

Open terminal

Type below commands

*cd
cd vsdflow/my_picorv32
qflow route picorv32
qflow sta picorv32
qflow backanno picorv32
leafpad log/sta.log*



### D5SK2 - MCQ2

log/post_sta.log

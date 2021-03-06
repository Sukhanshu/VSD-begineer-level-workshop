# VSD- Physical design using open-source EDA Tools
## Contents:
1. Study and review various components of RISC-V based picoSoC
2. Chip planning strategies and introduction to foundry library cells
3. Design and characterize one library cell using Magic Layout tool and ngspice
4. Pre-layout timing analysis and importance of good clock tree
5. Final steps for RTL2GDS

### The open source tools that are involved in this workshop are as follows

Yosys – for Synthesis, 
Graywolf – for Placement, 
Qrouter – for Routing, 
Netgen – for LVS, 
Magic – for Layout and Floorplanning, 
Qflow – RTL2GDS integration, 
OpenSTA & Opentimer -Pre-layout and Post-layout Static timing analysis

# DAY1 Study and review various components of RISC-V based picoSoC

***SKILL 1***
Introduction to QFN-48 Package, chip,pads,core,die and IP's,
***SKILL 2***
Introduction to RISC-V,
From Software applications to hardware
***SKILL 3***
Pre-requisites and RISC-V, picorv32 and picoSoC review,
Raven SoC
***SKILL 4***
Installation of basic EDA tools
# DAY 2 Chip planning strategies and introduction to foundry library cells
***SKILL 1***
utilization factor and aspect ration,
concept of pre-placed cells,
De-coupling capacitors,
power planning,
pin placement,
pin arrangement,
floorplanning
***SKILL 2***
netlist binding and initial place design,
estimated wire length and capacitance,
final placement optimization,
libraries and characterization
***SKILL 3***
inouts for cell design,
circuit design,
layout design,
characterization flow
***SKILL 4***
timing threshold,
propagation delay and transition time

# DAY 3 Design and characterize one library cell using Magic Layout tool and ngspice
DC analysis of inverter, transient analysis of inv, pulse width calculation, rise time , fall time calculation, LAyout formation on magic

# DAY 4 Pre-layout timing analysis and importance of good clock tree
Setup timing analysis, hold timing analysis, routing, Lee's algorithm, cross talk
# DAY 5 Final steps for RTL2GDS
Design rule check, paracitic extraction

### LABS

For the labs we are using the latest Google-SkyWater 130nm process node

Introduction to QFN-48 package, chips, pads, core, die, IP Introduction to RISC-V Architecture, picorv32 and picoSoC, RAVEN full chip and RAVEN SoC Introduction to open-source EDA Tools

1.Click on VSD IAT, Go to "Lab Instances". Then under "Links", click on the "link" icon. Click bottom left, System tools > LXTerminal. 2.Now type the command "yosys". What do you see next?
![05b8e0b9-ef22-4b2e-8a2f-b2db003f9fb8](https://user-images.githubusercontent.com/71768466/110246150-73ce9700-7f8c-11eb-929e-0980ff330a13.jpg)




*which sta*
![2021-03-04 (1)](https://user-images.githubusercontent.com/71768466/110247538-bc894e80-7f92-11eb-8283-b6f1fbc19caa.png)




*git clone https://github.com/kunalg123/vsdflow.git*



*cd vsdflow
./vsdflow spi_slave_design_details.csv
ls -ltr outdir_spi_slave/*
![2021-03-04 (2)__01](https://user-images.githubusercontent.com/71768466/110247598-03774400-7f93-11eb-96f6-b65a5b57b478.png)


Now type below command

*ls -ltr outdir_spi_slave | wc*

![2021-03-04 (4)__01](https://user-images.githubusercontent.com/71768466/110247621-20137c00-7f93-11eb-9e8e-1457e08054d0.png)




Calculation of area of layout.

*cd outdir_spi_slave
qflow display spi_slave*
It will open 2 windows "layout1" and "tkcon"

On "tkcon" window, type "box"and the area will be displayed in the command window.

![2021-03-04 (5)__01](https://user-images.githubusercontent.com/71768466/110247673-4fc28400-7f93-11eb-962d-d30dc08faecf.png)

![2021-03-04 (6)__01](https://user-images.githubusercontent.com/71768466/110247709-9d3ef100-7f93-11eb-95d8-cc9a52c90660.png)


![2021-03-04 (7)__01](https://user-images.githubusercontent.com/71768466/110247705-957f4c80-7f93-11eb-8f34-5d6ee5a32b3a.png)



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

![2021-03-04 (8)__01](https://user-images.githubusercontent.com/71768466/110247725-ae87fd80-7f93-11eb-9095-967146e4dd56.png)

![2021-03-04 (9)__01](https://user-images.githubusercontent.com/71768466/110247736-bcd61980-7f93-11eb-9f53-aac3284a2283.png)

![2021-03-04 (14)__01](https://user-images.githubusercontent.com/71768466/110247793-fb6bd400-7f93-11eb-8396-7b64e56d6c3f.png)

![2021-03-07__01](https://user-images.githubusercontent.com/71768466/110286889-a66ba480-800b-11eb-9478-3c3e3db64c0a.png)




Find area of the placed chip

Run the placement stage by setting the necessary options and performing the pin groupings.

Post completion of the placement stage, change to my_picorv32 folder and type the below command: qflow display picorv32 &

This will open layout and tkcon window In the layout window, select whole chip using below steps: Take cursor to bottom left and left-click. Take cursor to top right and right-click. Press Shift+i

This will select the whole layout Now in tkcon window, type "box".

You will get the area of the chip in microns.


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

*box*

![2021-03-04 (21)__01](https://user-images.githubusercontent.com/71768466/110247837-3f5ed900-7f94-11eb-896c-27f4bde56d74.png)

![2021-03-04 (22)__01](https://user-images.githubusercontent.com/71768466/110247877-6ae1c380-7f94-11eb-96bb-a5264fac3018.png)


SPICE Deck creation and, static and dynamic simulation for inverter, switching threshold Stick Diagram, Euler's path, abstract layouts Fn dimension derivation, layouts, scripting CMOS Fabrication Process

*cd
git clone https://github.com/kunalg123/ngspice_labs.git
cd ngspice_labs
cat inv.spice*
![2021-03-05__01](https://user-images.githubusercontent.com/71768466/110248075-57832800-7f95-11eb-98b0-b28ef8d82489.png)

Obtain the widths of the CMOS transistors

![2021-03-05 (2)__01](https://user-images.githubusercontent.com/71768466/110247954-bc8a4e00-7f94-11eb-8d1f-393975579c13.png)

![2021-03-05 (3)__01__01__01](https://user-images.githubusercontent.com/71768466/110247957-be541180-7f94-11eb-9228-fc4779c7cded.png)

![2021-03-05 (4)__01](https://user-images.githubusercontent.com/71768466/110247969-d166e180-7f94-11eb-8c90-810d410b90a3.png)


Obtain DC Transfer characteristics for different transistor widths and find switching threshold


*cd
cd ngspice_labs
ngspice inv.spice*
There will be terminal like below

ngspice 1 ->
On the above ngspice terminal, type below commands

*run
setplot dc1
plot out in*

![2021-03-05 (5)__01](https://user-images.githubusercontent.com/71768466/110247975-d7f55900-7f94-11eb-90ed-de2a64732c1e.png)




Go to labs, open terminal

Type below command

*leafpad inv.spice*

![2021-03-05 (7)__01](https://user-images.githubusercontent.com/71768466/110247998-f8bdae80-7f94-11eb-97ee-ccc495e0d25d.png)


Obtain Transient analysis and calculate the rise time

![2021-03-05 (11)__01](https://user-images.githubusercontent.com/71768466/110248038-2f93c480-7f95-11eb-8d99-37c09480a986.png)

![2021-03-05 (12)__01](https://user-images.githubusercontent.com/71768466/110248043-30c4f180-7f95-11eb-8a21-cf899e00c398.png)





Go to labs, type below commands

*cd
cd ngspice_labs
ngspice fn_prelayout.spice
ngspice 1 -> run
ngspice 1 -> setplot tran1
ngspice 1 -> plot out 1.25*

![2021-03-05 (12)__01](https://user-images.githubusercontent.com/71768466/110287062-ef235d80-800b-11eb-8b47-27c167d33fa5.png)



Obtain Transient analysis and calculate the rise time.

Go to labs, open terminal

Type below commands

*cd
cd ngspice_labs
magic -T min2.tech*

![2021-03-06 (2)__01](https://user-images.githubusercontent.com/71768466/110248104-784b7d80-7f95-11eb-9612-8be89149f73f.png)

This will open magic layout window and tkcon window

Go to tkcon window and type below command

*source draw_fn.tcl*





Go to labs, open terminal

Type below command

*cd
cd ngspice_labs
magic -T min2.tech fn_postlayout.mag &*

![foid](https://user-images.githubusercontent.com/71768466/110288907-b042d700-800e-11eb-8df8-2209ab53a291.PNG)




*cd
git clone https://github.com/kunalg123/ngspice_labs
cd ngspice_labs
cat inv_tran.spice*

![2021-03-06 (4)__01](https://user-images.githubusercontent.com/71768466/110248148-a761ef00-7f95-11eb-9073-6a95eb93cf5e.png)

![2021-03-06 (5)__01](https://user-images.githubusercontent.com/71768466/110248160-b34db100-7f95-11eb-9e6c-8c6029d54592.png)




Go to Day 4 (When you start Day 4 labs, system will enable Day 2 labs for you. Click on Desktop icon)

Open terminal and Type below commands

*cd
cd ngspice_labs
cat inv_tran.spice
ngspice inv_tran.spice*

![2021-03-06 (6)__01](https://user-images.githubusercontent.com/71768466/110248174-c82a4480-7f95-11eb-9fc8-f8c289cdb49d.png)

![2021-03-06 (7)__01](https://user-images.githubusercontent.com/71768466/110248202-e728d680-7f95-11eb-8231-5599626514dc.png)




Go to labs Open below file using "leafpad" or "less" or "vim" - whichever you are comfortable with)

*/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib*

![2021-03-06 (9)__01](https://user-images.githubusercontent.com/71768466/110248216-00318780-7f96-11eb-9114-2872e59c92a7.png)

![2021-03-06 (12)__01](https://user-images.githubusercontent.com/71768466/110248362-ad0c0480-7f96-11eb-9d77-8ca8077531dd.png)





Go to labs

Type below command

*cd
cd vsdflow/my_picorv32
leafpad picorv32.sdc*
Type below lines in the file picorv32.sdc file which you have just opened above

*create_clock -name clk -period 2.5 -waveform {0 1.25} [get_ports clk]*
Save and close the above file

Now type below command

*leafpad prelayout_sta.conf*
Type below lines in prelayout_sta.conf file which you have just opened above

*read_liberty /usr/local/share/qflow/tech/osu018/osu018_stdcells.lib
read_verilog synthesis/picorv32.rtlnopwr.v
link_design picorv32
read_sdc picorv32.sdc
report_checks*


Now type below command

*sta prelayout_sta.conf*

![2021-03-06 (13)__01](https://user-images.githubusercontent.com/71768466/110248385-ca40d300-7f96-11eb-9b18-47e72b3a18d4.png)

![2021-03-06 (14)__01](https://user-images.githubusercontent.com/71768466/110248392-d462d180-7f96-11eb-9db0-fef4ae43fc43.png)






![2021-03-06 (11)__01](https://user-images.githubusercontent.com/71768466/110248352-9bc2f800-7f96-11eb-9a6d-b55285e0288a.png)


Perform all steps in D4SK2 - MCQ11

You are now at below "sta" terminal

*%*
Type below command in above terminal

*set_propagated_clock [all_clocks]
report_checks*

![D5SK2](https://user-images.githubusercontent.com/71768466/110287621-d7000e00-800c-11eb-9d90-845f555817aa.PNG)





Perform all steps in D4SK4 - MCQ3

Type below command

*report_checks -path_delay min -digits 4*

![111111](https://user-images.githubusercontent.com/71768466/110287992-5ab9fa80-800d-11eb-929c-3cc579e7ffcc.png)

![112222](https://user-images.githubusercontent.com/71768466/110288144-93f26a80-800d-11eb-832c-e0319a8c67dc.png)



Day 5 labs : Routing and DRCs - Lee's Maze Algorithm Introduction to SPEF - Different Representations of Parasitics PnR Tutorials


Obtain Pre-layout and Post-layout frequencies

Open terminal

Type below commands

*cd
cd vsdflow/my_picorv32
qflow route picorv32
qflow sta picorv32
qflow backanno picorv32
leafpad log/sta.log*

![2021-03-07 (2)__01](https://user-images.githubusercontent.com/71768466/110288202-a79dd100-800d-11eb-8db7-fbe8d41a8c11.png)



*log/post_sta.log*

![post_sta](https://user-images.githubusercontent.com/71768466/110289184-13346e00-800f-11eb-88ad-b2b5bd066918.PNG)


## Conclusion
We successfully executed the PD or PnR (Place and Eoute) flow. Obtained VTC of the design, Created the magic layout of design. Performed static timing analysis. 


### Acknowledgement
@kunalg123 
 Co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd.




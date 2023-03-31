# Improvements in OpenROAD-flow-scripts
## presented by:
## P.D.Divya sree
# 1.INTRODUCTION
ORFS is a short form for OpenROAD Flow Scripts. OpenROAD flow scripts and OpenLANE are flow-controllers supported by the OpenROAD Design project repository.
ORFS provides a collection of open-source tools required for automating the digital design from synthesis to layout for complete RTL to GDSII flow, includes Synthesis, Placement and Routing (PnR), Static Timing Analysis (STA), Design Rule check (DRC) and Layout versus Schematic (LVS) check.The OpenROAD Flow project aims to automate digital circuit design with no human intervention and achieve a 24-hour turnaround time. 

I added ?:(conditional operator) in place of if else to decrese the number of lines in code, Increses the system performance and decrease the system runtime.I also used ORFS to generate the GDSII file for riscv2i. I also modified the global routing files to decrease the routing time, which in turn reduces the CPU usage time to a significant extent, keeping in mind the DRC rules.
# 2.IMPROVEMENTS
## CTS file is updated using :?(conditional operator) used  instead of ifelse statement
The suggested improvement is to update the ifelse statements with :? operator. During the execution time I felt that the cpu takes more elapsed time to perform,where the performance of the decreases.so, I request to delete multiple  ifelse statements in files like floorplanning, royting ,layout and replace it with :?. so,I created a pull request regards this by changing the code in CTS file.
file where i make changes
       make_DESIGN_CONFIG=./designs/asap7/riscv32i
# changes in the CTS file to decrease CPU usage time
The suggested improvement is shown below
### before
![before](https://user-images.githubusercontent.com/114659084/229130180-42179d38-3c9d-4227-9285-973144a772ff.png)
### After
![final_cts_file](https://user-images.githubusercontent.com/114659084/229130562-bea1c816-86cc-4bc4-af13-4b3aa26d5a46.png) 


## Effect of updatation
### before
Elapsed time: 0:05.58[h:]min:sec. CPU time: user 5.01 sys 0.28 (94%). Peak memory: 480916KB.
cp results/asap7/ibex/base/6_1_merged.gds designs/asap7/riscv32i
![timing](https://user-images.githubusercontent.com/114659084/229171613-e542d1fb-41ef-45d4-83f5-9bc8deff6b6a.jpg)



#### After
Elapsed time: 0:05.09[h:]min:sec. CPU time: user 4.77 sys 0.31 (99%). Peak memory: 481532KB.
cp results/asap7/ibex/base/6_1_merged.gds results/asap7/riscv32i/base/6_final.gds

![after_tim](https://user-images.githubusercontent.com/114659084/229171971-aeae13a8-d6d8-4bdb-aa00-4590db460d86.png)
# OpenROAD GUI diagrams
## OpenROAD GUI
To see the GUI interface of every stage of Physical Design for a particular design in OpenROAD, we can use the GUI command.

For Floorplan GUI, run below command

    make gui_floorplan
    
![image](https://user-images.githubusercontent.com/42606968/227088581-ddbbc993-ba09-4ce4-97e8-e2d96de79dca.png)

For Placement GUI, run below command

    make gui_place

![image](https://user-images.githubusercontent.com/42606968/227088833-38c22793-f414-4e00-80f6-ad54b61b42e5.png)

For Clock Tree Synthesis (CTS), run below command

    make gui_cts
    
![image](https://user-images.githubusercontent.com/42606968/227089033-e5807951-1b1f-44ea-ab68-c679f69aafe9.png)

For Routing, run below command

    make gui_route
    
![image](https://user-images.githubusercontent.com/42606968/227089208-22fbd42f-9703-4771-992e-b21e88874245.png)

For Final Stage, run below command  

    make gui_final
     
![image](https://user-images.githubusercontent.com/42606968/226173763-e286d7c0-78db-4cb2-b9a7-b792e40adf0b.png)

In all the above stages, a highly interative and colourful GUI screen will pop-up with all the details.

## Viewing reports using the TCL commands in OpenROAD GUI

    report_power

In my case, the reported power is as below,  

    Group                  Internal  Switching    Leakage      Total
                              Power      Power      Power      Power (Watts)
    ----------------------------------------------------------------
    Sequential             4.50e-04   5.99e-05   3.16e-06   5.13e-04  32.5%
    Combinational          5.59e-04   4.96e-04   9.98e-06   1.06e-03  67.5%
    Macro                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
    Pad                    0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
    ----------------------------------------------------------------
    Total                  1.01e-03   5.56e-04   1.31e-05   1.58e-03 100.0%
                              63.9%      35.2%       0.8%

# 3.CONCLUSION
 I think my contribution to the openroad will useful .In this openroad contest I have learnt lot of things. I have learnt some about Physical Design and it's flow from scratch. I have learnt how open source tools work.  I also learnt to how to use git to collaborate with other VSD developers.I have lernt how to give pull request and how to give git push.I think this work may helpful to my future.






















This documentation is available at [https://openroad.readthedocs.io/en/latest/](https://openroad.readthedocs.io/en/latest/)

## Build locally

### Requires:
- Python 3.x
- Pip
- `virtualenv`

### Install prerequisites:

``` shell
virtualenv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Build:

``` shell
make html
```

### Check for broken links:

``` shell
make checklinks
```

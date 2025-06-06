# Tool Command Language (TCL) Workshop
# Sponsored by VSD
______________________________________________
# Contents (Day 1 - Day 5)
``` Table of Contents ```

- [Day 1 - Day 1: Introduction to TCL and VSDSYNTH Toolbox Usage](#section-1)
  - [TCL_D1_SK1 - Introduction](#subsection-11)
    - [TCL_D1_SK1 L0 - Introduction to TCL task](#sub-subsection-111)
    - [TCL_D1_SK1 L1 - Introduction to sub-task](#sub-subsection-112)
  - [TCL_D1_SK2 - Sub-Task One: VSDSYNTH Toolbox usage scenarios](#subsection-12)
    - [TCL_D1_SK2 L1 - Scenario 1 - User doesn't provide an input CSV file](#sub-subsection-121)
    - [TCL_D1_SK2 L2 - Scenarios 2 & 3 - User providing incorrect CSV or typing "-help"](#sub-subsection-122)
   
    
      
- [Day 2: Variable Creation and Processing Constraints from CSV](#section-2)
  - [TCL_D2_SK1 - Sub-Task Two - From CSV to format \[1\] and SDC - Variable Creation](#subsection-21)
    - [TCL_D2_SK1 L1 - Various tasks involved in format conversion](#sub-subsection-211)
    - [TCL_D2_SK1 L2 - Auto-Create variables using matrix and arrays](#sub-subsection-212)
    - [TCL_D2_SK1 L3 - Initialize variables for auto-creation variables task](#sub-subsection-213)
    - [TCL_D2_SK1 L4 - Auto creation of the first variable - DesignName](#sub-subsection-214)
    - [TCL_D2_SK1 L5 - Auto creation of variables complete](#sub-subsection-215)
    - [TCL_D2_SK1 L6 - Variable Creation DEMO using TCL](#sub-subsection-216)
  - [TCL_D2_SK2 - Sub-Task Two - From CSV to format\[1\] and SDC - Processing constraints, CSV](#subsection-22)
    - [TCL_D2_SK2 L1 - Checking the existence of files and folders mentioned in design_details.csv](#sub-subsection-221)
    - [TCL_D2_SK2 L2 - Convert constraints.csv file to a matrix object](#sub-subsection-222)
    - [TCL_D2_SK2 L3 - Compute row number using complex matrix processingn](#sub-subsection-223)
    - [TCL_D2_SK2 L4 - DEMO for computing row numbers](#sub-subsection-224)
  
   
- [Day 3: Processing Clock and Input Constraints](#section-3)
  - [Sub-Task Two - From CSV to format\[1\] and SDC - Processing clock constraints](#subsection-31)
    - [Algorithm to identify the column number for clock latency constraints](#sub-subsection-311)
    - [Start writing clock latency constraints in the SDC file](#sub-subsection-312)
    - [Complete clock latency constraints and clock slew constraints in the SDC file](#sub-subsection-313)
    - [Code to create clock constraints with clock period and duty cycle](#sub-subsection-314)
    - [DEMO for creating complete clock constraints](#sub-subsection-315)
  - [Sub-Task Two - From CSV to format[1] and SDC - Processing input constraints](#subsection-32)
    - [Introduction to the task of differentiating between bits and a bus](#sub-subsection-321)
    - [Algorithm to categorize input ports as bits and bussed](#sub-subsection-322)
    - [File access and pattern creation steps](#sub-subsection-323)
    - [Regular expression and regular substitute to get fixed space strings](#sub-subsection-324)
    - [Demo for grepping input ports from all verilogs and reformatting for fixed space](#sub-subsection-325)
    - [Read, split, uniquify, sort, and join input ports to remove duplication](#sub-subsection-326)
    - [Evaluate the length of the string and Demo of bits/bussed differentiation script](#sub-subsection-327)
    - [Demo for input constraints generation and bits/bussed differentiation](#sub-subsection-328)
   
- [Day 4: Complete Scripting and Yosys Synthesis Introduction](#section-4)
  - [Full script for download and Conclusion](#subsection-41)
    - [Constraints generation logic for the output port and Conclusion!!](#sub-subsection-411)
  - [Introduction to Yosys synthesis tool usage](#subsection-42)
    - [Example of a memory module RTL description](#sub-subsection-421)
    - [Memory functionality and Synthesis using Yosys](#sub-subsection-422)
    - [Components and Gate level netlist description of Synthesized memory](#sub-subsection-423)
    - [Memory Write operation discussed in detail](#sub-subsection-424)
    - [-Memory Read operation and TCL scripting agenda](#sub-subsection-425)
  - [Hierarchy check and error handling script creation for Yosys](#subsection-43)
    - [Script to do a hierarchy check](#sub-subsection-431)
    - [Demo for hierarchy check script generation](#sub-subsection-432)
    - [Demo for error handling concept in hierarchy check](#sub-subsection-433)
    - [Error handling script for hierarchy check](#sub-subsection-434)
    - [Demo for error handling script](#sub-subsection-435)


- [Day 5: Advanced Scripting Techniques and Quality of Results Generation](#section-5)
  - [Synthesis main file scripting and output file editing](#subsection-51)
    - [Synthesis script creation and demo](#sub-subsection-511)
    - [Need and script to edit Yosys output netlist](#sub-subsection-512)
    - [Demo to edit output netlist and Introduction to 'procs'](#sub-subection-513)
  - [World of 'Procs'](#subsection-52)
    - [Redirect stdout proc and demo of TCL array command](#sub-subsection-521)
    - ['set_multi_cpu_usage' proc](#subsection-522)
    - [Demo for 'set_multi_cpu_usage' proc](#sub-subsection-523)
    - [read_lib and read_verilog proc demo](#sub-subsection-524)
  - [read_sdc proc - interpret clock generation constraints](#subsection-53)
    - [Read SDC file and replace square brackets by 'null'](#sub-subsection-531)
    - [Evaluate clock period and clock port name from processed SDC](#sub-subsection-532)
    - [Evaluate duty cycle and create clock in opentimer format](#sub-subsection-533)
    - [Demo to convert constraints from SDC format to opentimer format](#sub-subsection-534)
  - [read_sdc proc - interpret clock generation constraints](#subsection-54)
    - [Grep clock latency and port name from SDC file](#sub-subsection-541)
    - [Convert set_clock_latency SDC to opentimer format](#sub-subsection-542)
    - [Demo to convert set_clock_latency in SDC to arrival_time in opentimer](#sub-subsection-543)
    - [Script and demo convert transition and input delay to opentimer format](#sub-subsection-544)
    - [Script and demo to convert output SDC constraints to opentimer format](#sub-subsection-545)
  - [read_sdc proc - interpret clock generation constraints](#subsection-55)
    - [Script to expand bussed input ports for arrival time constraints](#sub-subsection-551)
    - [Script and demo to convert all bussed constraints to bit-blasted](#sub-subsection-552)
    - [Opentimer configuration file creation](#sub-subsection-553)
  - [read_sdc proc - interpret clock generation constraints](#subsection-56)
    - [Script to obtain STA runtime](#sub-subsection-561)
    - [Script to obtain WNS and FEP for reg2out violations](#sub-subsection-562)
    - [-Script and demo for instance count, WNS, and FEP for setup and hold](#sub-subsection-563)
    - [Script and demo for report formatting](#sub-subsection-432)
  - [Conclusion](#subsection-57)
    - [Conclusion and acknowledgments](#sub-subsection-571)
_______________________________________________________________________
<a name="section-1"></a>
## Day 1: Introduction to TCL and VSDSYNTH Toolbox Usage
<a name="subsection-11"></a>
### TCL_D1_SK1 - Introduction
<a name="sub-subsection-111"></a>
#### TCL_D1_SK1 L0 - Introduction to TCL task
We are trying to build a task to build a user interface which will take excel sheet as an input and a data sheet as output.
We are using .csv format as excel file format, where csv stands for comma seperated value.

  ![sampleip](https://github.com/user-attachments/assets/8555fb79-ff05-46ea-9461-9c8b07e4cbe4)


The excel sheet consists of top designn name, output path directory, source code or rtl, path of .lib file, path of constraints.
The user interface we are trying to build, will take the .csv(excel) file as the input and it will produce all the necessary results as shown below.
![agenda](https://github.com/user-attachments/assets/ad11a914-6e13-4b6e-8e85-0e4c3c4a5cff)

#### TCL_D1_SK1 L1 - Introduction to sub-task

Create command and pass .csv from Unix shell to TCL script. If we check the path of the input .csv file below
![pathtocsv](https://github.com/user-attachments/assets/a2943a53-3d9a-4ec9-ae3a-21b12b907ecc)
Now we are trying to create a command named as vsdsynth that will take .csv file as an input and passes it to the tclbox.
Next task is to convert all the inputs to a format that is format[1] and .sdc format and pass it to the synthesis tool 'Yosys'.
![format1](https://github.com/user-attachments/assets/20e8eb61-911b-4a0d-ac99-7a3f007f5c6b)
![sdc](https://github.com/user-attachments/assets/65fe8b30-f61b-4ae5-bcf8-c68fd49d466b)
Next task is to convert the format[1] and .sdc to format[2] and pass it to timing tool OpenTimer tool.
OpenTimer accepts following type of input format:

![input2OT](https://github.com/user-attachments/assets/7715eed1-6af0-448e-a60e-3eeabb570aab)
Final task is to generate the output which looks like below
![op1](https://github.com/user-attachments/assets/309538ce-dc19-4687-a8f3-f87f02c10de1)


<a name="subsection-12"></a>
### TCL_D1_SK2 - Sub-Task One: VSDSYNTH Toolbox usage scenarios
<a name="sub-subsection-121"></a>
#### TCL_D1_SK2 L1 - Scenario 1 - User doesn't provide an input CSV file
We can discuss some scenarios based on the inputs given by the user.
Case -1: User has not provided .csv file as an input.
Case -2: User has provided a .csv file, which does not exist.
Case -3: User wants to get more knowledge regarding the command using -help switch.
In the below snippet, to access an argument we use $argv and $#argv represents the number of arguments that are passed. So, if the number of arguments is not equal to 1, then it will print the following message.

![arg1](https://github.com/user-attachments/assets/df441f7f-0cce-41f8-b561-20dd9fc7d000)

When there is no input .csv file, the value of $#argv is equal to zero, from the below script we can check

![snippet](https://github.com/user-attachments/assets/aa55fd2d-4c7b-498f-a5ab-252da6f5746f)
Now, if we give the below command in the termianl

                     ./vsdsynth
It will give the following output

![nocsv](https://github.com/user-attachments/assets/5e1615dc-4c3a-46d8-b9db-3e9fbdd31676)

<a name="sub-subsection-122"></a>
#### TCL_D1_SK2 L2 - Scenarios 2 & 3 - User providing incorrect CSV or typing "-help"
Let's discuss case -2, for user has provided an incorrect .csv file. We can write the following  part of the code.

![miss1](https://github.com/user-attachments/assets/7daffd4a-ecc7-4d4a-aa11-027ee666ca7e)

Now, if we give ./vsdsynth command, we get the following output

![wcsv](https://github.com/user-attachments/assets/aca59f70-7d07-4bf0-8ceb-d18f49888baa)


Now, for case -3, where the user wants to get more knowledge regarding the command using -help switch. We can modify the code as below:

![else1](https://github.com/user-attachments/assets/fe61f343-58b6-48cb-8520-aa95217deec2)

Now, if we give the following command
                 
                 ./vsdsynth -help
It will give the following output

![helpo](https://github.com/user-attachments/assets/d023d0be-a2e5-44bd-9cd3-649471e361e5)

<a name="section-2"></a>
## Day 2: Variable Creation and Processing Constraints from CSV
<a name="subsection-21"></a>
### TCL_D2_SK1 - Sub-Task Two - From CSV to format \[1\] and SDC - Variable Creation
<a name="sub-subsection-211"></a>
#### TCL_D2_SK1 L1 - Various tasks involved in format conversion]
Now, we are trying to convert all the inputs into format[1] and .sdc format, we would like to pass these files to 'Yosys' tool.
For this we need to start create variables. And we have to check whether the files or the paths mentioned in .csv file exists or not. We need to convert the constraints from the .csv file to .sdc format.
Then we will be reading all the netlist files.
After that we will be creating main synthesis script in format[2]
Then pass this to Yosys tool.
<a name="sub-subsection-212"></a>
#### TCL_D2_SK1 L2 - Auto-Create variables using matrix and arrays
We are trying to pass the input.csv file to the vsdsynth tclbox using the following command
         
          ./vsdsynth openMSP430_design_details.csv 

Now inside vsdsynth we have to modify like below

          tclsh vsdsynth.tcl $argv[1]

This is how we pass the .csv file to the tcl script.
Whenever we are passing any arguments to the vsdsynth.tcl will be considered as $argv, which can have index 0,1,2 etc. We can do it using lindex command
         
        set filename [lindex $argv 0]


![10](https://github.com/user-attachments/assets/4f4c8572-7057-4c88-a4a8-a89cf009fb9e)

Now, our goal is to auto create the variables.

Now, from the input.csv file, we are trying to read the variables in a matrix format, which then we would like to convert as array. 

  ![flow1](https://github.com/user-attachments/assets/2c4d51ad-03d0-4a52-adfb-0ace4bcf7199)


<a name="sub-subsection-213"></a>
#### TCL_D2_SK1 L3 - Initialize variables for auto-creation variables task
So we have created a shell script named as vsdsynth and using the shell script we are trying to invoke the tcl script. Now, we need to check how to access the .csv file through the tcl script. Now we require some packages to extract the .csv file, we can start using the below commands. We are trying to create a matrix using struct::matrix m command.

        set filename [lindex $argv 0]
        package require csv
        package require struct::matrix
        struct::matrix m
        set f [open $filename]
	csv::read2matrix $f m , auto
	close $f
	set columns [m columns]
	m add columns $columns
	m link my_arr
	set num_of_rows [m rows]
 We can open any file using the open command, but prior to that it has to be set as a variable or file id given as f. Now, f can be used as a file opend in read mode.

![ipcsv2](https://github.com/user-attachments/assets/647644fa-d8ce-4541-84fc-3a8c1591ef15)

 
 Now, if we try to open the csv file using vim, we can see that it is nothing but a comma seperated value file.
 
 ![vcsv1](https://github.com/user-attachments/assets/87b9ccc9-0d8c-40b9-a518-923324721bb7)

 Then, we are trying to convet the matrix m to an array my_arr using link command.

<a name="sub-subsection-214"></a>
#### TCL_D2_SK1 L4 - Auto creation of the first variable - DesignName
Now, we have to loop throug the entire array.
![loop1](https://github.com/user-attachments/assets/58c5fcce-d839-41ea-a6d1-377a9645a124)

Now, we can see the algorithm below

![algo1](https://github.com/user-attachments/assets/2ffefc53-4cfc-4d07-be05-ad8d0c264869)

Now, we can build the logicg as below,

                 if{$i==0}
		 set [strig map {" " " "} $my_arr(o,i)] $my_arr(1,i) 
   Let's discuss the operation of the string map command.

                             string map {_parui _vsd} ratul_parui


                             Before string map: ratul_parui
			     After string map:  ratul_vsd
			     
So, we have replaced _parui by _vsd using string map command.
<a name="sub-subsection-215"></a>
#### TCL_D2_SK1 L5 - Auto creation of variables complete
Now, let's procced with the code

![code14](https://github.com/user-attachments/assets/1a43bae4-35e0-4764-bc01-4a4c62e69b2d)

Now, we can see for i=0,1,2,3 respectively

![code12](https://github.com/user-attachments/assets/28d99ee8-e5d7-46ec-8b91-38341917f061)

Now, let us analyze the below command

	        [file normalize $my_arr(1,i)]
Here, $my_arr(1,i) is an file path. Let us discuss what the normalize command do:

                Before file normalize = ~/Desktop/Vsdflow
		After file normalize = home/VsdUser/Desktop/Vsdflow
  So, the file normalize command expands the reference path to a absolute path
  After the execution of the while loop, we get all the file paths assigned to the respective variables.
<a name="sub-subsection-216"></a>
#### TCL_D2_SK1 L6 - Variable Creation DEMO using TCL
Now, we have written the vsdflow.tcl file that we have passed through the vsdsynth tclbox using shell script.

![code11](https://github.com/user-attachments/assets/6c1b836c-b26f-48f7-9bf0-86d4816ec4fc)



Now, if we try to run the below command

      ./vsdsynth openMSP430_design_details.csv
We can see the following output

![op15](https://github.com/user-attachments/assets/1a219850-21ea-4bda-8692-f1ebec3a48fd)


we have our desired output for the given input.csv file

Now we have to chek all the directory paths exist or not.
<a name="subsection-22"></a>
### TCL_D2_SK2 - Sub-Task Two - From CSV to format\[1\] and SDC - Processing constraints, CSV
<a name="sub-subsection-221"></a>
#### TCL_D2_SK2 L1 - Checking the existence of files and folders mentioned in design_details.csv
Now to check whether the output directory exists or not, we can give the following set of commands.
![ex1](https://github.com/user-attachments/assets/ae8f8c6f-c3b6-4a01-9634-195436584878)

The command

          file isdirectory
will return boolean value 0/1
Now, the above set of commands create an output directory, if the output directory is not present.
Similarly, we can check for the netlist directory. 

![ex2](https://github.com/user-attachments/assets/6d0438af-c43c-44c7-998b-ed9a46d65326)

Similarly, for the constraints directory

![ex3](https://github.com/user-attachments/assets/f4d1f345-94b3-4355-a1f2-d64877a66eb5)

<a name="sub-subsection-222"></a>
#### TCL_D2_SK2 L2 - Convert constraints.csv file to a matrix object
Now, let us suppose, we have removed the output directory.

                       rm -rf outdir_openMSP430
Then the above script will show messgae: creating output directory.
![msg1](https://github.com/user-attachments/assets/d3cb64f2-400e-40c5-8c38-80607a1cbf56)



Below is the input constraints file in .csv format
![contr1](https://github.com/user-attachments/assets/9e059b9d-e9c4-4446-9edd-19247e082700)

Now, we will be converting this .csv file to a matrix using the below commands

![matr1](https://github.com/user-attachments/assets/c56d17fd-5607-4c8e-9d04-742e52a1d5d7)

We are trying to assign the opened .csv file in a variable chan. Now we are converting the constaints file into a matrix.

<a name="sub-subsection-223"></a>
#### TCL_D2_SK2 L3 - Compute row number using complex matrix processingn
Now, we are trying to get the number of rows and columns using the below commands

![commnds23](https://github.com/user-attachments/assets/d3da0568-1ee9-4dbf-a404-0de6e2d13ed4)

Now, if we try to run

     ./vsdsynth openMSP430_design_details.csv
We have the following  output as row as 57 and column as 11 numbers.

![rowsacols](https://github.com/user-attachments/assets/1567d9b3-2f75-43ec-b33a-f3a859d92228)



<a name="sub-subsection-224"></a>
#### TCL_D2_SK2 L4 - DEMO for computing row numbers
Let us modify the code as below

![code234](https://github.com/user-attachments/assets/4c58ab12-36a1-430d-844f-015aa24f8900)

Now, we are getting the following output

![op234](https://github.com/user-attachments/assets/c44ac6b5-f01d-4216-b2d4-67155752941a)

Now from the .csv constraints file, we would like to convert it to a .sdc format.

![csv123](https://github.com/user-attachments/assets/ed9bcf37-33f6-4a6b-9ced-b03fdf2f16ee)


<a name="section-3"></a>
## Day 3: Processing Clock and Input Constraints
<a name="subsection-31"></a>
### Sub-Task Two - From CSV to format[1] and SDC - Processing clock constraints
Now, we would like to restrict the search space in between the selected area:
![snap311](https://github.com/user-attachments/assets/76a983ea-e764-447d-8fa5-6bc212f51029)

Now, let us open the .sdc file written in the outdir
![sdc1](https://github.com/user-attachments/assets/88283522-0b98-452a-81a8-4d34a4a412d2)

<a name="sub-subsection-311"></a>
#### Algorithm to identify the column number for clock latency constraints



Let us, check the following code:
  
    set sdc_file [open $OutputDirectory/$DesignName.sdc "w"]
    set i [expr {$clock_start+1}]
    set end_of_ports [expr {$input_ports_start-1}]
    puts "\nInfo-SDC: Working on clock constraints....."
    while { $i < $end_of_ports } {
We have assigned the filename .sdc in write mode to a variable as sdc_file.
Since, previously, we have found that $clock_start value is 0, i is set to 1. And, $input_ports_start is 4, end_of_ports is set to 3. We are setting a new variaable as clock_early_rise_delay_start, and it's value is assigned to 3. Which exactly matches the column number of early_rise_delay in .csv file.
Now, we would like to write data in sdc_file variable.
<a name="sub-subsection-312"></a>
#### Start writing clock latency constraints in the SDC file
Inside the while loop we would like to print the data required as expected. for that we use, below set of codes
   
    set sdc_file [open $OutputDirectory/$DesignName.sdc "w"]
    set i [expr {$clock_start+1}]
    set end_of_ports [expr {$input_ports_start-1}]
    puts "\nInfo-SDC: Working on clock constraints....."
    while { $i < $end_of_ports } {
    puts -nonewline $sdc_file "\nset_clock_latency -source -early -rise [constraints get cell $clock_early_rise_delay_start $i] \[get_clocks [constraints get cell 0 $i]\]"
    set i [expr {$i+1}]
Now, the above puts command prints the desired data in the sdc_file variable, finally appends to .sdc file. set_clock_latency -source -early -rise gets printed as it is. Then let us discuss [constraints get cell $clock_early_rise_slew_start $i] part, where constraints is a matrix name, get cell is a package command and $clock_early_rise_slew_start, $i are column and row, which are set to be 3 and 0. So, the contents of cell number [3,0] gets printed due to the square braces, which does substituion. Whenever there is a square bracet, it's get trated as a tcl command, so to print it as it is, we need backslash( \ ).
Now, i is the value of row, we need to increase it to 2, to go to next row.
<a name="sub-subsection-313"></a>
#### Complete clock latency constraints and clock slew constraints in the SDC file
Now, we can modify the above code snippet and add new lines to print in the file like below

![smp312](https://github.com/user-attachments/assets/58b91be7-6ede-4def-acab-3f84ef258ea4)

Now, we have added lines for example: set_clock_latency -source -early -fall, for that we need to change to column $clock_early_fall_delay_start, which is set to 4. Similarly $clock_late_rise_slew_start is set to 5.

<a name="sub-subsection-314"></a>
#### Code to create clock constraints with clock period and duty cycle

Now, let us define the time period and duty cycle of a clock. The standard clock definition is shown below

    create_clock -name dco_clk -period 1500 -waveform {0 750} [get_ports dco_clk]
Now, in the input constraints .csv file the duty cycle is mentioned as 50% for column=2, row =1.  

    puts -nonewline $sdc_file "\ncreate_clock -name [constraints get cell 0 $i] -period [constraints get cell 1 $i] -waveform \{0 [expr {[constraints get cell 1 $i]*[constraints get cell 2 $i]/100}]\} \[get_ports [constraints get cell 0 $i]\]"

We need to access the row = 1 and col = 1, where the frequency value is given. 
In the above part of the code we have calculated the waveform part from the duty cycle using the below command

    [expr {[constraints get cell 1 $i]*[constraints get cell 2 $i]/100}]
               1500                   *        50                 /100 = 750
            
![code3451](https://github.com/user-attachments/assets/7ecaed83-7c38-4326-91ad-9b1b738e3b48)

   


<a name="sub-subsection-315"></a>
#### DEMO for creating complete clock constraints
Now, let us try to execute the above part of the code and try to print the present working clock
![cd344](https://github.com/user-attachments/assets/0f7f3a6e-51f5-43e6-9e0d-dc80ec593c43)
So, after running the command we have the following output
![op3444](https://github.com/user-attachments/assets/15018822-a99b-4e51-a7b6-5a4c6e72ea8f)

Now, if we open te .sdc file, it will show the contents written inside it.

![sdc23](https://github.com/user-attachments/assets/1f8f1169-a221-4217-a9db-6114c7e80efe)


<a name="subsection-32"></a>
### Sub-Task Two - From CSV to format[1] and SDC - Processing input constraints
<a name="sub-subsection-321"></a>
#### Introduction to the task of differentiating between bits and a bus
Now to get the bus names we need to use wildcards.
Now, let us limit the search space to the highlited area.
![csv344](https://github.com/user-attachments/assets/de866c6e-ce68-4a29-b64f-60b3023a6a42)

Now, we need to set some varibales to get the respective columns for early_rise_delay, early_fall_delay etc.
We, need to check all the verilog files in the directory.
![vdir](https://github.com/user-attachments/assets/138abcbe-1b71-4edf-b6a2-e2ce59a18ad4)

Now, we need to grep the cpu_en in all the verilog files, using the following command

    grep cpu_en /home/vsduser/vsdsynth/verilog/*.v
Which will give the following output
![op2334](https://github.com/user-attachments/assets/2b946994-4b6c-46b9-9251-392000cd2ec9)

<a name="sub-subsection-323"></a>
#### Algorithm to categorize input ports as bits and bussed

<a name="sub-subsection-323"></a>
#### File access and pattern creation steps
Now, to get all the .v contents of the directory, we need to use the glob command.
The demo command is shown below

    glob -dir $NetlistDirectory *.v
Now, we are trying to open a temp file in write mode, to do temporary work.

Now, we would like to access each and every netlist file using foreach loop.

![forech3444](https://github.com/user-attachments/assets/6a35dada-dc84-45cb-b12c-422add9aa0e2)


Using the below command, we are trying to open each and every verilog file and assign them to a variable.

    set fd [open $f]

Now, from the $fd we need to read each and every line using gets command. Where -1, stands for the end of line. Now, we would like to set pattents based on the cell names.

<a name="sub-subsection-324"></a>
#### Demo for grepping input ports from all verilogs and reformatting for fixed space
 We are setting a pattern based on the delimiter ;
![scrpyt34](https://github.com/user-attachments/assets/f2473525-f2a6-413d-b237-e016e6b478d6)

 
<a name="sub-subsection-324"></a>
#### Regular expression and regular substitute to get fixed space strings
Now, let us try to explain the below comand

    set patternj1 " [constraints get cell 0 $i]
    regexp -all -- $patternl $line
  regexp will try to find the pattern in all the respective files. So, we have put this inside a while loop, to iterate it few number of times. Now, we are trying to set a pattern2 using the below command

    set pattern2 [lindex [split $line ";"] 0]
Now, there could be multiple spaces in pattern2, so we are trying to split pattern2 based on spaces.

    [lindex [split $pattern2 "\S+"] 0]
For our current example, the above part of the code retuens input
Now, let us put it inside a if statement, so we are trying to match input with input

    if {[regexp -all {input} [lindex [split $pattern2 "\S+"] 0]]}
Similarly, we can get 0,1,2 index elements using lindex. 
Now, let us define a new pattern s1, given below
![pattrn324](https://github.com/user-attachments/assets/1291cc81-d1f8-4e3b-9428-ac54a4cb90e3)

Now, let us try to substitute multiples spaces by a single space, using the below command

    regsub -all {\s+} $s1 ""
Where {\s+} stands for multiple spaces n regsub. Now, we are are writing in the tmp file. Then it closes the file $fd. 
<a name="sub-subsection-325"></a>
#### Demo for grepping input ports from all verilogs and reformatting for fixed space
Now, let us print the present file, using puts command. Also we are trying to print the pattern found.
![codiff324](https://github.com/user-attachments/assets/1ab4b38f-59a3-4274-8ac9-89f0e67db4a1)

Now, if we execute the above code, we have the output as

![op3454](https://github.com/user-attachments/assets/0508ee45-95f5-466b-a7bf-47bb0049b183)


<a name="sub-subsection-326"></a>
#### Read, split, uniquify, sort, and join input ports to remove duplication

<a name="sub-subsection-327"></a>
#### Evaluate the length of the string and Demo of bits/bussed differentiation script
<a name="sub-subsection-328"></a>
#### Demo for input constraints generation and bits/bussed differentiation










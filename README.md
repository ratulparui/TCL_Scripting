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
Now, we are trying to get the number of rows as 57 and columns as 11 using the below commands

![commnds23](https://github.com/user-attachments/assets/d3da0568-1ee9-4dbf-a404-0de6e2d13ed4)

Now, if we try to run

     ./vsdsynth openMSP430_design_details.csv
We have the following  output as row and column numbers.

![rowsacols](https://github.com/user-attachments/assets/1567d9b3-2f75-43ec-b33a-f3a859d92228)

<a name="sub-subsection-224"></a>
#### TCL_D2_SK2 L4 - DEMO for computing row numbers

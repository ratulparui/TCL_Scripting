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

<a name="sub-subsection-214"></a>
#### TCL_D2_SK1 L4 - Auto creation of the first variable - DesignName
<a name="sub-subsection-215"></a>
#### TCL_D2_SK1 L5 - Auto creation of variables complete
<a name="sub-subsection-216"></a>
#### TCL_D2_SK1 L6 - Variable Creation DEMO using TCL

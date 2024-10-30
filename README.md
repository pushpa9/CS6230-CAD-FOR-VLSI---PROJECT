# CS6230-CAD-FOR-VLSI---PROJECT 1 (MULTIPLY ACCUMULATE)

### A MAC operation, performed on 3 numbers A, B, and C, is formulated as shown below.
##### MAC = A*B + C

### This has 2 different folders, each containing bluespec verilog code and cocotb testbench for 2 different data types:
##### 1. Non-pipelined MAC 
##### 2. Pipelined MAC 

### 2 different data types are:
##### 1. S1. (A: int8 , B: int8 , C: int32) -> (MAC: int32)
##### 2. S2. (A: bf16, B: bf16, C: fp32) -> (MAC: fp32)

### Structure: 
##### The project is uploaded as a zip file which contains 2 folders.
##### 1. Mac_nonpipeline : Uses ripple carry adder and shift and add multiplier to implement mac. There is a mac.bsv file, test_mac.py file which implements cocotb testbench to verify the design. Test cases are uploaded in mac_verif folder and and a model_mac.py is created to implement coverage (result in yaml file).
#### 2. Mac_pipeline : This implements 2 stage pipeline with FIFOs, 1st being multiply and second being adder. The folder structure is same as mac_nonpipeline.
##### The coverage includes walking 1, walking 0 and random set of inputs. 
##### The detailed report of microarchitecture, design and verification methodologies is uploaded as CAD_for_VLSI_2024_Project_1.pdf

### This project is made by Pushpa Chaudhary (EE21B109) and Fardeen Razif (EE21B046) 
##### Seperate contributions:
##### 1. Mac_pipeline and Mac_nonpipeline bsv design : Pushpa
##### 2. Cocotb testbench (test_mac.py) and model_mac.py - Pushpa
##### 3. General debugging - Both
##### 4. Report - Fardeen




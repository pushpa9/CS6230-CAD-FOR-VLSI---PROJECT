# CS6230-CAD-FOR-VLSI---PROJECT 1 (MULTIPLY ACCUMULATE)

### A MAC operation, performed on 3 numbers A, B, and C, is formulated as shown below.
• MAC = A*B + C

### This has 2 different folders, each containing bluespec verilog code and cocotb testbench for 2 different data types:
### 1. Non-pipelined MAC 
### 2. Pipelined MAC 

### 2 different data types are:
### 1. S1. (A: int8 , B: int8 , C: int32) -> (MAC: int32)
### 2. S2. (A: bf16, B: bf16, C: fp32) -> (MAC: fp32)

### There are 5 predefined methods in the top-level interface to the module, namely, A, B, C,
S1_or_S2, and MAC. No additional methods are required. Please feel free to rename the
methods to make your BSV code more readable. For instance, method get_A(…) can
be used to load the value of ‘A’ into the design.

### The verification of the top module has to be done using the cocotb framework, as described
during the demo session. Sample test cases have been provided via 4 files per supported format
(int8 and bf16). Each file contains 1000 different values, which are specified in binary format
and detailed below.
• S1 (int8): A_binary.txt and B_binary.txt contain 8-bit signed integer values. C_binary.txt
contains 32-bit signed integer values. MAC_binary.txt contains the 32-bit signed integer
values that are expected to be produced by the S1 MAC operation.
• S2 (bf16): A_binary.txt and B_binary.txt contain bfloat16 values. C_binary.txt contains
the fp32 values. MAC_binary.txt contains the fp32 values that are expected to be
produced by the S2 MAC operation.

# Project 1 : Pipelined and Non-pipelined Multiply Accumulate Unit (MAC)

### Pushpa Chaudhary - EE21B109, Fardeen Razif - EE21B046

## Design Overview

The project is uploaded as a `.zip` file containing two folders:

1. **Mac_nonpipeline**:  
   - **int32**:  
     - Implements MAC using a ripple carry adder (`ripple_carry_adder` function) and a shift-and-add multiplier (`mult` function).  
     - In the `mult` function, absolute values of `a` and `b` are computed, and the product is calculated. A 2’s complement of the product is taken based on the signs of `a` and `b`.  
   - **bfloat16**:  
     - Multiplication is implemented using the `custom_mult` function, and addition is handled using the `float_add` function.  
     - In the `custom_mult` function:  
       1. Extract sign, exponent, and mantissa from inputs.  
       2. Multiply mantissas, normalize the product, and adjust the exponent.  
       3. Combine the sign, exponent, and mantissa, round off the answer to `bfloat16`, and append 16 trailing bits to make `fp32`.  
     - In the `float_add` function:  
       1. Extract sign, exponent, and mantissa from inputs.  
       2. Align exponents by right-shifting the mantissa of the smaller exponent.  
       3. Add or subtract mantissas based on signs, normalize the result, adjust the exponent, and combine everything together.  

2. **Mac_pipeline**:  
   - Implements a two-stage pipeline using `mkPipelineFIFOs`.  
   - The first stage handles multiplication, and the second stage handles addition (implemented using rules: `rl_mult_stage` and `rl_adder_stage`).  
   - Functions are the same as in `Mac_nonpipeline`, but FIFOs are used to enqueue inputs and dequeue outputs every clock cycle instead of using registers.

---

## Verification Methodology

- A `test_mac.py` file implements the cocotb testbench, taking given or random test cases.  
- Test cases are uploaded in the `mac_verif` folder.  
- A `model_mac.py` is created to provide expected outputs for test cases, enabling coverage analysis (results stored in a `.yaml` file).  

**Note**:  
- `s = 1` → `int32`  
- `s = 0` → `bfloat16`

### Verification Details

1. **Mac_nonpipeline**:  
   - Takes 3 clock cycles to generate an output after inputs are provided.  
   - All 1,050 given test cases are verified.  
   - Coverage includes Walking `1` pattern, Walking `0` patter, Random inputs (expected outputs computed using `model_mac.py`).  

2. **Mac_pipeline**:  
   - Inputs are provided every clock cycle.  
   - Takes 4 clock cycles to generate the first output, after which outputs are generated every clock cycle.  
   - All 1,000 given test cases are verified.  
   - Coverage includes random inputs (expected outputs computed using `model_mac.py`).  
 

## How to Run

* Download the `.zip` file. It would have `mac_pipeline` and `mac_nonpipeline` folders. 
* Enter into any one of the directories.
* Enter `make clean` command to wipe off any previous compilations and then `make generate_verilog` command to compile and generate a Verilog file for the BSV design.
* `Mac_verif` folder inside both directories has `test_mac.py` as the cocotb testbench.
  * `test_mac.py` verifies the design for given test cases and any random test case. 
* Enter `make simulate` command to run this `.py` testbench. 
  * It will automatically start verifying all given test cases and will fail if any assertions fail. 
  * Make sure to change `s` accordingly (`s = 1` for `int32`, `s = 0` for `bfloat16`).
* This also executes coverage. 
  * It will automatically start executing walking `1` and walking `0` input patterns, which will be verified using the output generated from `model_mac.py` file.

### Status
1. **int32**:
   * Pipelined design: 
     * Code - completed
     * Verification - completed
   * Non-pipelined design: 
     * Code - completed
     * Verification - completed

2. **bfloat16**:
   * Pipelined design: 
     * Code - completed
     * Verification - completed
   * Non-pipelined design: 
     * Code - completed
     * Verification - completed


### Separate Contributions

1. **Mac_pipeline and Mac_nonpipeline BSV design**: Pushpa  
2. **Cocotb testbench (`test_mac.py`) and `model_mac.py`**: Pushpa  
3. **General debugging**: Both  
4. **Report**: Fardeen
5. **Readme**: Pushpa

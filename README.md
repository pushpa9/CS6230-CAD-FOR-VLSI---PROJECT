# Project 1 : Pipelined and Non-pipelined Multiply Accumulate Unit (MAC)

### Pushpa Chaudhary - EE21B109, Fardeen Razif - EE21B046

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

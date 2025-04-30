# FPGA Quantum Algorithm Emulation

This repository contains Vivado projects implementing two fundamental quantum‐algorithm emulators on a Xilinx Kintex UltraScale+ FPGA:

* Quantum Fourier Transform (QFT) Core

* Grover’s Search Core

Both designs are written in SystemVerilog, fully parameterizable, and wrapped with UART interfaces for easy host‐side data capture.



**FPGA Target:**

* Xilinx Kintex UltraScale+

* Part: XCKU3P-FFVA676-3-E

* Speed Grade: -3

* Package: FFVA676

**Development Tools:**

* Xilinx Vivado 2022.2.2 (Windows 64-bit)

  * Synthesis, Implementation, and Timing Closure

  * Power Estimation (Vector-less and SAIF-driven)

  * Resource Utilization Reporting

**UART Interface:**

* Baud Rate: 115200 baud

* Data Format: 8-N-1

* Outputs are streamed MSB-first, real part then imaginary part, in 24-bit fixed-point (Q1.22) chunks.

## Usage

### Open Vivado Project

vivado -mode gui qft/qft.xpr # orvivado -mode gui grover/grover.xpr
### Build Flow

1. Run Synthesis

2. Run Implementation

3. Generate Bitstream

4. Hardware Programming

5. Load the bitstream onto the evaluation board.

6. Toggle the START input to begin the transform/search.

7. Observe the UART output on a serial terminal to verify results.

### Simulation & Testbench

* Open `tb_qft5_emulate.sv` or `tb_grover_search.sv` in Vivado’s simulator.

* Run functional simulation and inspect waveforms or console‐printed results.

### Power & Resource Analysis

After implementation, use Vivado Tcl:

open_run impl_1report_utilization -hierarchical -file util.rptreport_power       -file pw.rpt
* Review `util.rpt` for registers, LUTs, CARRY8, DSPs, etc.

* Review `pw.rpt` for total, dynamic, and static power.



## References

* Lee, H., Kim, J., & et al. An FPGA‐Based Quantum Circuit Emulator, IEEE Trans. on Computers, 2016.

* Xilinx Vivado Design Suite User Guides and Datasheets.

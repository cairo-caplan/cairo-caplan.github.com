---
layout: post
category : GSOC2017
tagline: "Supporting tagline"
comments : "true"
tags : [intro, beginner, jekyll, tutorial]
---
{% include JB/setup %}

On this posts I will talk about the options of RISC V projects I consider to integrate on the LimeSDR project.

As I previously said on my [presentation]({% post_url 2017-06-01-LimeSDR-and-RISCV %}) post about, my plan is to implement a wrapper to a SoC, where I can choose which RISC V implementation (or NIOS) I will use during compilation. My original propose was to use the Pulpino for FPGA, but, considering its complexity plus my non-familiarity with SystemVerilog I also list others:

## RISC V choices


### Orca

![Orca as a Quartus/Qsys component]({{ site.url }}/assets/orca-riscv.gif)

[Orca](https://github.com/VectorBlox/orca) is a small RISC V implementation made by Vectorblox under a BSD license, it implements the RV32I or RV32IM ISA and is coded in VHDL.

A nice thing about it is that they it comes prepared to be easily inserted on
systems using proprietary tools or IP cores from FPGA vendors, for example it provides
a tcl script to import it as component inside Qsys. Its data and instructions bus interfaces also can be chosen Wishbone, Avalon or AXI standards
The code comes with an [example system](https://github.com/VectorBlox/orca/tree/master/systems/de2-115) for the DE2-115 board, where Orca is
instantiated inside an Altera Qsys file. There is a nice presentation on RISC V website from January 2016 you can check [here]{https://riscv.org/wp-content/uploads/2016/01/Wed1200-2016-01-05-VectorBlox-ORCA-RISC-V-DEMO.pdf}.

### PicoRV32

[PicoRV32](https://github.com/cliffordwolf/picorv32) is a RISC V CPU designed by [Clifford Wolf](http://www.clifford.at/) (the same creator of Yosys!) that can be configured as RV32E, RV32I, RV32IC, RV32IM, or RV32IMC compatible CPU. It was concepted with a reduced size in mind, and also can achieve higher operations frequencies (claiming 250-450 MHz on 7-Series Xilinx FPGAs).

Another differential of it is its simplicity, the CPU is defined in a single Verilog file and optionally can be interfaced into a AXI bus.
It is licensed under the ISC license.

### Pulpino

![Orca as a Quartus/Qsys component](http://www.pulp-platform.org/wp-content/uploads/2016/05/DSC_1121_lrg_mod.jpg)


Pulpino

it implements the RV32IMC instructions set and is coded on SystemVerilog.

---
layout: post
category : GSOC2017
tagline: "Supporting tagline"
comments : "true"
tags : [intro, beginner, jekyll, tutorial]
---


This post relates my tentative to implement the Pulpino on an Altera device. I
created a new Quartus project solely for the purpose to make Pulpino synthesizable,
without messing with the LimeSDR gateware for now.



Quartus seems to dislike unnamed generates, allowed on standard Verilog, as clearly
described on this [link](http://quartushelp.altera.com/14.1/mergedProjects/msgs/msgs/evrfx_veri_block_id_required.htm) of Quartus help.

{% highlight bash %}
Error (10644): Verilog HDL error at ram_mux.sv(74): this block requires a name
Error (10644): Verilog HDL error at ram_mux.sv(114): this block requires a name
Error (10112): Ignored design unit "ram_mux" at ram_mux.sv(11) due to previous errors
Error (10644): Verilog HDL error at peripherals.sv(134): this block requires a name
Error (10112): Ignored design unit "peripherals" at peripherals.sv(16) due to previous errors
Error (10644): Verilog HDL error at axi_node_intf_wrap.sv(154): this block requires a name
Error (10644): Verilog HDL error at axi_node_intf_wrap.sv(212): this block requires a name
Error (10112): Ignored design unit "axi_node_intf_wrap" at axi_node_intf_wrap.sv(13) due to previous errors
Error (10228): Verilog HDL error at apb_bus.sv(72): module "APB_BUS" cannot be declared more than once
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(55) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(57) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(61) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(65) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(69) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(73) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(77) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(81) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(85) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10170): Verilog HDL syntax error at periph_bus_wrap.sv(89) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10112): Ignored design unit "periph_bus_wrap" at periph_bus_wrap.sv(13) due to previous errors
Error (10644): Verilog HDL error at sp_ram.sv(54): this block requires a name
Error (10112): Ignored design unit "sp_ram" at sp_ram.sv(11) due to previous errors
Error (10644): Verilog HDL error at apb_node_wrap.sv(57): this block requires a name
Error (10112): Ignored design unit "apb_node_wrap" at apb_node_wrap.sv(23) due to previous errors
Error (10644): Verilog HDL error at apb_node.sv(61): this block requires a name
Error (10112): Ignored design unit "apb_node" at apb_node.sv(23) due to previous errors
Error (10170): Verilog HDL syntax error at core2axi.sv(254) near text: ";";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10644): Verilog HDL error at core2axi.sv(259): this block requires a name
Error (10112): Ignored design unit "core2axi" at core2axi.sv(16) due to previous errors
Error (10170): Verilog HDL syntax error at hwloop_regs.sv(102) near text: "for";  expecting "endmodule". Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10112): Ignored design unit "riscv_hwloop_regs" at hwloop_regs.sv(25) due to previous errors
Error (10644): Verilog HDL error at hwloop_controller.sv(59): this block requires a name
Error (10112): Ignored design unit "riscv_hwloop_controller" at hwloop_controller.sv(25) due to previous errors
Error (10644): Verilog HDL error at cs_registers.sv(318): this block requires a name
Error (10112): Ignored design unit "riscv_cs_registers" at cs_registers.sv(34) due to previous errors
Error (10170): Verilog HDL syntax error at alu_div.sv(89) near text: "<<";  expecting an operand. Check for and fix any syntax errors that appear immediately before or at the specified keyword. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (10112): Ignored design unit "riscv_alu_div" at alu_div.sv(26) due to previous errors
Error (10644): Verilog HDL error at alu.sv(60): this block requires a name
Error (10644): Verilog HDL error at alu.sv(69): this block requires a name
Error (10644): Verilog HDL error at alu.sv(304): this block requires a name
Error (10644): Verilog HDL error at alu.sv(361): this block requires a name
Error (10112): Ignored design unit "riscv_alu" at alu.sv(28) due to previous errors
Error (10644): Verilog HDL error at alu.sv(953): this block requires a name
Error (10644): Verilog HDL error at alu.sv(965): this block requires a name
Error (10644): Verilog HDL error at alu.sv(973): this block requires a name
Error (10644): Verilog HDL error at alu.sv(962): this block requires a name
Error (10112): Ignored design unit "alu_ff" at alu.sv(929) due to previous errors
Error (10644): Verilog HDL error at alu.sv(1017): this block requires a name
Error (10644): Verilog HDL error at alu.sv(1023): this block requires a name
Error (10644): Verilog HDL error at alu.sv(1029): this block requires a name
Error (10644): Verilog HDL error at alu.sv(1035): this block requires a name
Error (10112): Ignored design unit "alu_popcnt" at alu.sv(1005) due to previous errors
Error (10644): Verilog HDL error at axi_regs_top.sv(426): this block requires a name
Error (10644): Verilog HDL error at axi_regs_top.sv(424): this block requires a name
Error (10644): Verilog HDL error at axi_regs_top.sv(434): this block requires a name
Error (10112): Ignored design unit "axi_regs_top" at axi_regs_top.sv(92) due to previous errors
Error (10644): Verilog HDL error at axi_address_decoder_AW.sv(113): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AW.sv(111): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AW.sv(122): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AW.sv(120): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AW.sv(130): this block requires a name
Error (10112): Ignored design unit "axi_address_decoder_AW" at axi_address_decoder_AW.sv(42) due to previous errors
Error (10644): Verilog HDL error at axi_address_decoder_AR.sv(93): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AR.sv(91): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AR.sv(102): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AR.sv(100): this block requires a name
Error (10644): Verilog HDL error at axi_address_decoder_AR.sv(110): this block requires a name
Error (10112): Ignored design unit "axi_address_decoder_AR" at axi_address_decoder_AR.sv(42) due to previous errors
Error: Quartus Prime Analysis & Synthesis was unsuccessful. 68 errors, 10 warnings
	Error: Peak virtual memory: 1226 megabytes
	Error: Processing ended: Tue Jun 27 00:37:40 2017
	Error: Elapsed time: 00:00:25
	Error: Total CPU time (on all processors): 00:00:43
Error (293001): Quartus Prime Full Compilation was unsuccessful. 70 errors, 10 warnings

{% endhighlight bash %}

So I started labeling all this for-generate sections with this errors. Like on the following line, from:

{% highlight verilog %}
  ...
  for(i0 = 0; i0 < IN0_RATIO; i0++)
  begin
    ...
{% endhighlight verilog %}

to:

{% highlight verilog %}
  ...
  for(i0 = 0; i0 < IN0_RATIO; i0++)
  begin : for_gen
    ...
{% endhighlight verilog %}


In pulpino/rtl/includes/apb_bus.sv, from
{% highlight verilog %}
`define APB_ASSIGN_SLAVE(lhs, rhs)     \
    assign lhs.paddr    = rhs.paddr;   \
    assign lhs.pwdata   = rhs.pwdata;  \
    assign lhs.pwrite   = rhs.pwrite;  \
    assign lhs.psel     = rhs.psel;    \
    assign lhs.penable  = rhs.penable; \
    assign rhs.prdata   = lhs.prdata;  \
    assign rhs.pready   = lhs.pready;  \
    assign rhs.pslverr  = lhs.pslverr;
{% endhighlight verilog %}

To:

{% highlight verilog %}
`define APB_ASSIGN_SLAVE(lhs, rhs)     \
    assign lhs.paddr    = rhs.paddr;   \
    assign lhs.pwdata   = rhs.pwdata;  \
    assign lhs.pwrite   = rhs.pwrite;  \
    assign lhs.psel     = rhs.psel;    \
    assign lhs.penable  = rhs.penable; \
    assign rhs.prdata   = lhs.prdata;  \
    assign rhs.pready   = lhs.pready;  \
    assign rhs.pslverr  = lhs.pslverr
{% endhighlight verilog %}



In pulpino/ips/axi/core2axi/rtl/core2axi.sv, line 254, from

{% highlight verilog %}
  endgenerate;
{% endhighlight verilog %}

to:

{% highlight verilog %}
  endgenerate
{% endhighlight verilog %}


And the creation of a generate around a loop on the /ips/riscv/hwloop_regs.sv,
line 101, from:

{% highlight verilog %}
genvar k;
  for (k = 0; k < N_REGS; k++) begin : for_gen
    assign hwlp_counter_n[k] = hwlp_counter_q[k] - 1;
  end

  always_ff @(posedge clk, negedge rst_n)
  begin : HWLOOP_REGS_COUNTER
    if (rst_n == 1'b0)
    begin
      hwlp_counter_q <= '{default: 32'b0};
    end
    else
    begin
      for (i = 0; i < N_REGS; i++)
      begin
        if ((hwlp_we_i[2] == 1'b1) && (i == hwlp_regid_i)) begin
          hwlp_counter_q[i] <= hwlp_cnt_data_i;
        end else begin
          if (hwlp_dec_cnt_i[i] && valid_i)
            hwlp_counter_q[i] <= hwlp_counter_n[i];
        end
      end
    end
  end
{% endhighlight verilog %}


{% highlight verilog %}
generate
	genvar k;
	  for (k = 0; k < N_REGS; k++) begin : for_gen
	    assign hwlp_counter_n[k] = hwlp_counter_q[k] - 1;
	  end

	  always_ff @(posedge clk, negedge rst_n)
	  begin : HWLOOP_REGS_COUNTER
	    if (rst_n == 1'b0)
	    begin
	      hwlp_counter_q <= '{default: 32'b0};
	    end
	    else
	    begin
	      for (i = 0; i < N_REGS; i++)
	      begin
	        if ((hwlp_we_i[2] == 1'b1) && (i == hwlp_regid_i)) begin
	          hwlp_counter_q[i] <= hwlp_cnt_data_i;
	        end else begin
	          if (hwlp_dec_cnt_i[i] && valid_i)
	            hwlp_counter_q[i] <= hwlp_counter_n[i];
	        end
	      end
	    end
	  end
endgenerate
{% endhighlight verilog %}

And, as Quartus don't support streaming operations as the bit orderr reversion on
the ALU, in the file




Please also note that, if you choose pulpino as your top entity, Quartus will
complain because the name of the verilog module, pulpino_top, is different from
the name of the file, top.sv. On this case the top entity may be selected from a
list on Assignements > Settings > General  , as in the picture:

![Pulpino Top]({{ site.url }}/assets/pulpino_top.gif)



ips/riscv/prefetch_buffer.sv - 143
ips/riscv/exc_controller.sv - 97



Even after doing this modifications, and before changing the Xilinx memories to
generic ones, I got the following Quartus error:


{% highlight bash %}
Problem Details
Error:
Internal Error: Sub-system: VRFX, File: /quartus/synth/vrfx/verific/vhdl/vhdlvalue_elab.cpp, Line: 3865
_values && pos < _values->Size()
Stack Trace:
   0x12cf6f: vrfx_altera_assert(bool, char const*, int, char const*) + 0x20 (synth_vrfx)
   0x2c3c8a: VhdlCompositeValue::SetValueAt(unsigned int, VhdlValue*) + 0x4e (synth_vrfx)
   0x2f455b: VhdlIdRef::AssignPartial(VhdlValue*, VhdlConstraint*, VhdlValue*, VhdlValue*, Net*, Array const*, unsigned int, VhdlDataFlow*) + 0x591 (synth_vrfx)
   0x2edeae: VhdlIdRef::Assign(VhdlValue*, VhdlDataFlow*, Array*) + 0x316 (synth_vrfx)
   0x2f0232: VhdlIndexedName::Assign(VhdlValue*, VhdlDataFlow*, Array*) + 0x72 (synth_vrfx)
   0x3129b2: VhdlSignalAssignmentStatement::Execute(VhdlDataFlow*, VhdlBlockConfiguration*) + 0x1ae (synth_vrfx)
   0x31951b: VhdlIfStatement::Execute(VhdlDataFlow*, VhdlBlockConfiguration*) + 0x555 (synth_vrfx)
   0x318a57: VhdlProcessStatement::Execute(VhdlDataFlow*, VhdlBlockConfiguration*) + 0x1cf (synth_vrfx)
   0x2ba0de: VhdlArchitectureBody::Elaborate(VhdlBlockConfiguration*) + 0xfc (synth_vrfx)
   0x2baa2d: VhdlEntityDecl::CoreElaborate(VhdlSecondaryUnit*, char const*, VhdlBlockConfiguration*) + 0x453 (synth_vrfx)
   0x2c000e: VhdlEntityDecl::Elaborate(char const*, Array*, Map*, VhdlBlockConfiguration*) + 0x3f0 (synth_vrfx)
   0x14f3dc: VRFX_VERIFIC_VHDL_ELABORATOR::elaborate(BASEX_ELABORATE_INFO*) + 0x1c8 (synth_vrfx)
   0x144d77: VRFX_ELABORATOR::elaborate(BASEX_ELABORATE_INFO*) + 0x97 (synth_vrfx)
   0x176bf7: SGN_FN_LIB::elaborate(BASEX_ELAB_INFO_CORE*) const + 0x157 (synth_sgn)
   0x17f96e: SGN_FN_LIB::start_vrf_flow() const + 0xe (synth_sgn)
   0x17ffc4: SGN_FN_LIB::start(SGN_WRAPPER_INFO*) + 0x574 (synth_sgn)
   0x184741: SGN_EXTRACTOR::single_module_extraction(HDB_INSTANCE_NAME*, HDB_ENTITY*, SGN_WRAPPER_INFO*) const + 0x101 (synth_sgn)
   0x18c498: SGN_EXTRACTOR::recursive_extraction(HDB_INSTANCE_NAME*, SGN_WRAPPER_INFO*, char const*) + 0x1f8 (synth_sgn)
   0x18d456: SGN_EXTRACTOR::recurse_into_newly_extracted_netlist(HDB_ENTITY*, HDB_INSTANCE_NAME*, unsigned long, SGN_WRAPPER_INFO*) + 0x546 (synth_sgn)
   0x18c57c: SGN_EXTRACTOR::recursive_extraction(HDB_INSTANCE_NAME*, SGN_WRAPPER_INFO*, char const*) + 0x2dc (synth_sgn)
   0x18d456: SGN_EXTRACTOR::recurse_into_newly_extracted_netlist(HDB_ENTITY*, HDB_INSTANCE_NAME*, unsigned long, SGN_WRAPPER_INFO*) + 0x546 (synth_sgn)
   0x18c57c: SGN_EXTRACTOR::recursive_extraction(HDB_INSTANCE_NAME*, SGN_WRAPPER_INFO*, char const*) + 0x2dc (synth_sgn)
   0x18d456: SGN_EXTRACTOR::recurse_into_newly_extracted_netlist(HDB_ENTITY*, HDB_INSTANCE_NAME*, unsigned long, SGN_WRAPPER_INFO*) + 0x546 (synth_sgn)
   0x18c57c: SGN_EXTRACTOR::recursive_extraction(HDB_INSTANCE_NAME*, SGN_WRAPPER_INFO*, char const*) + 0x2dc (synth_sgn)
   0x192763: SGN_EXTRACTOR::extract() + 0x3a3 (synth_sgn)
   0x1a30f0: sgn_qic_full(CMP_FACADE*, std::vector<std::string, std::allocator<std::string> >&, std::vector<double, std::allocator<double> >&) + 0x440 (synth_sgn)
    0x20559: qsyn_execute_sgn(CMP_FACADE*, std::vector<std::string, std::allocator<std::string> >&, std::string const&, THR_NAMED_PIPE*, THR_NAMED_PIPE*) + 0x159 (quartus_map)
    0x3c1f1: QSYN_FRAMEWORK::execute_core(THR_NAMED_PIPE*, THR_NAMED_PIPE*) + 0x231 (quartus_map)
    0x3feec: QSYN_FRAMEWORK::execute() + 0xc2c (quartus_map)
    0x1c3fb: qexe_standard_main(QEXE_FRAMEWORK*, QEXE_OPTION_DEFINITION const**, int, char const**) + 0x888 (comp_qexe)
    0x34a3c: qsyn_main(int, char const**) + 0x13c (quartus_map)
    0x3fe60: msg_main_thread(void*) + 0x10 (ccl_msg)
     0x602c: thr_final_wrapper + 0xc (ccl_thr)
    0x3ff1c: msg_thread_wrapper(void* (*)(void*), void*) + 0x62 (ccl_msg)
    0x51199: mem_thread_wrapper(void* (*)(void*), void*) + 0x99 (quartus_map)
     0x8def: err_thread_wrapper(void* (*)(void*), void*) + 0x27 (ccl_err)
     0x63f2: thr_thread_wrapper + 0x15 (ccl_thr)
    0x42122: msg_exe_main(int, char const**, int (*)(int, char const**)) + 0xa3 (ccl_msg)
    0x206e5: __libc_start_main + 0xf5 (c.so.6)


End-trace


Executable: quartus
Comment:
None

System Information
Platform: linux64
OS name: SUSE LINUX
OS version: 42

Quartus Prime Information
Address bits: 64
Version: 15.1.2
Build: 193
Edition: Standard Edition

{% endhighlight bash %}

It comes during the Elaboration step of the Serial UART module of Pulpino, the
only part coded in VHDL. Taking some hints from [a post on Altera Forum](https://www.alteraforum.com/forum/showthread.php?t=44793), which tells that
maybe the problem is that the compiler thinks that the memory address is out of bounds.
I tracked the origin of the error to the file ips/apb/apb_uart/slib_fifo.vhd,
then I modified to put some checking before assigning indexes/address to the
memory structure, from:

{% highlight verilog %}

-- FIFO memory process
FF_MEM: process (RST, CLK)
begin
		if (RST = '1') then
				iFIFOMem(2**SIZE_E-1 downto 0) <= (others => (others => '0'));
				Q <= (others => '0');
		elsif (CLK'event and CLK = '1') then
				if (WRITE = '1' and iFULL = '0') then
						iFIFOMem(to_integer(iWRAddr(SIZE_E-1 downto 0))) <= D;
				end if;
				Q <= iFIFOMem(to_integer(iRDAddr(SIZE_E-1 downto 0)));
		end if;
end process;

{% endhighlight verilog %}

To:

{% highlight verilog %}

-- FIFO memory process
FF_MEM: process (RST, CLK)
	variable address : integer range 0 to 2**SIZE_E-1;
begin
		if (RST = '1') then
				iFIFOMem <= (others => (others => '0'));
				Q <= (others => '0');
		elsif (CLK'event and CLK = '1') then
			if (WRITE = '1' and iFULL = '0') then
				if to_integer(iWRAddr(SIZE_E-1 downto 0)) <= 2**SIZE_E-1 then
					address := to_integer(iWRAddr(SIZE_E-1 downto 0));
					iFIFOMem(address) <= D;
				end if;
			end if;
			if to_integer(iRDAddr(SIZE_E-1 downto 0)) <= 2**SIZE_E-1 then
				address := to_integer(iRDAddr(SIZE_E-1 downto 0));
					Q <= iFIFOMem(address);
				end if;
		end if;
end process;

{% endhighlight verilog %}



And then finally:

{% highlight bash %}

Error (12006): Node instance "sp_ram_i" instantiates undefined entity "xilinx_mem_8192x32". Make sure that the required user library paths are specified correctly. If the project contains EDIF Input Files (.edf), make sure that you specified the EDA synthesis tool settings correctly. Otherwise, define the specified entity or change the calling entity. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error (12006): Node instance "sp_ram_i" instantiates undefined entity "xilinx_mem_8192x32". Make sure that the required user library paths are specified correctly. If the project contains EDIF Input Files (.edf), make sure that you specified the EDA synthesis tool settings correctly. Otherwise, define the specified entity or change the calling entity. The Altera Knowledge Database contains many articles with specific details on how to resolve this error. Visit the Knowledge Database at https://www.altera.com/support/support-resources/knowledge-base/search.html and search for this specific error message number.
Error: Quartus Prime Analysis & Synthesis was unsuccessful. 2 errors, 128 warnings
	Error: Peak virtual memory: 1324 megabytes
	Error: Processing ended: Wed Jun 28 02:35:56 2017
	Error: Elapsed time: 00:00:23
	Error: Total CPU time (on all processors): 00:00:45
Error (293001): Quartus Prime Full Compilation was unsuccessful. 4 errors, 128 warnings

{% endhighlight bash %}

After this modifications, Quartus doesn't complain anymore about errors, but it
doesn't compile either, in a way the Analysis & Sinthesis stage never finishes.

I searched the root of this isse, from pulpino_top, to core_region and then to
sp_ram_wrap that uses the sp_ram module. Quartus showd the message:


{% highlight bash %}

Info (12127): Elaborating entity "sp_ram_wrap" for the top level hierarchy
Info (12128): Elaborating entity "sp_ram" for hierarchy "sp_ram:sp_ram_i"
Info (10008): Verilog HDL or VHDL information: EDA Netlist Writer cannot regroup multidimensional array "mem" into its bus

{% endhighlight bash %}

This time, though, the analysis slowly finished in 10 min. To my surprise
Quartus understood the module as a BIG register file instead of block memory.
As shown on the next picture:

![sp_ram as logic]({{ site.url }}/assets/sp_ram_as_logic.gif)




Error (10106): Verilog HDL Loop error at sp_ram_wrap.sv(129): loop must terminate within 5000 iterations
Error (12152): Can't elaborate user hierarchy "simple_ram:sp_ram_i"

https://www.alteraforum.com/forum/showthread.php?t=21989

Assignment -> Settings -> Compiler Settings -> Advanced Settings (Synthesis) -> Iteration limit for constant Verilog loops
The default value is 5000, change it to anything over 32768 as, say, 150000.




<center><img src="{{ site.url }}/assets/pulpino_standalone_fitter.gif"></center>
<center>Pulpino standalone resource utilization on Quartus Fitter.</center><br>

<center><img src="{{ site.url }}/assets/quartus_bug_pulpino.gif"></center>
<center>Quartus Bug on EDA Netlist Writer for the Pulpino standalone project.</center><br>



 {% if page.comments %}
 <div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = https://cairo-caplan.github.io/;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = "cairo-2011-12-29-jekyll-introduction"; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://cairo-caplan-github.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>


 {% endif %}

# vsd_rtldesign_synthesis
Record of RTL design and Synthesis Workshop using SKY130 Technology conducted by Vlsi System Design (VSD) on 27 May 2026
-------------------------------------------------------------------------------------------------------------------------
-testbench - applies stimulus (test vectors) tp design to test its functionality
-Simulatr (iverilog) looksfor changes in signlas of input , simulates design
-design - actual verilog code
-Output of simulator is a vcd file 
(design+tb->iverilog->vcd(value change dump)->gtkwave(view waveform))
<img width="1073" height="655" alt="image" src="https://github.com/user-attachments/assets/0913a8b2-21a8-4d1b-95bd-9b5f30039761" />
------------------------------------------------------------------------
 mkdir vlsi
 cd vlsi
 mkdir vsdflow
 git clone  https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
 <img width="1225" height="520" alt="image" src="https://github.com/user-attachments/assets/af856d85-dd1d-4a44-b1e1-19747e4b077a" />
    cd vlsi
   cd vsdflow //didnt store anything in this ignore
   ls 
   cd sky130RTLDesignAndSynthesisWorkshop
   ls -ltr
   cd my_lib // has verilog_models
   ls
   cd lib   :This file contain the  Sky130 Standard Cell library // outside my_lib
   cd ..
   cd verilog_model :Content of verilog models
   <img width="1233" height="651" alt="image" src="https://github.com/user-attachments/assets/730ea9e5-8aab-4735-84e3-9c8ef692c2de" />
      cd sky130RTLDesignAndSynthesisworkshop
   ls
   cd verilog_files
   <img width="1319" height="620" alt="image" src="https://github.com/user-attachments/assets/6de215b2-6bc9-433e-9716-90f5107f544d" />
   in verilog_files::
   iverilog good_mux.v tb_good_mux.v
./a.out

<img width="1784" height="87" alt="image" src="https://github.com/user-attachments/assets/3674e323-1b76-4a30-b3b9-82f366b3eb69" />
gtkwave tb_good_mux.vcd
<img width="1919" height="787" alt="image" src="https://github.com/user-attachments/assets/b6308b67-38e6-4b14-9d6c-22026a29467f" />
dont forget to appebd variables and zoom out



-The $dumpvars system task in Verilog is used to specify which variables and hierarchy levels should be recorded in a Value Change Dump (VCD) file for later waveform analysis. It is typically used in conjunction with $dumpfile, which specifies the filename for the output

-$dumpvars(level, list_of_variables_or_modules);

-level: An integer specifying the depth of the hierarchy to dump.
 - 0: Dumps all variables in the specified module and all of its sub-modules (recursive).
 - 1: Dumps only the variables in the specified module, ignoring sub-modules.
 - n: Dumps variables in the specified module and all sub-modules up to \(n-1\) levels deep

netlist - A Verilog netlist is a low-level structural description of a digital circuit that details the exact electronic components used and how they are connected. It serves as a machine-generated "blueprint," typically created by synthesis tools, replacing abstract code with instantiated logic gates and flip-flops. tool used - yosys.

read_verilog - read design
read_librty - read .lib 
write_verilog -  make netlist
netlist is design in form of cells in .lib
---------------------------------------------
netlist + tb(sm as rtl tb) in  iverilog  gives vcd file which put into gtkwave gives u waveform which shud be same as observed using rtl syn
----------------------------------------------
rtl- > gate level translation =  syn
.lib - collection of logical modules - and or nor nand and their diff flavours / specifications
combinational delay - maxm speed of ops 
tclk > tcq_a(prop d of ffa) + tcomb + tsetup_b
setup timr - 
----------------------------------------------------------------------------
hold time-  The minimum amount of time a data signal must remain stable after a clock edge so a flip-flop can reliably capture it


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
seeing files using cat command (gvim wasnt working)
<img width="1109" height="692" alt="image" src="https://github.com/user-attachments/assets/bf39fb99-94b3-46dc-8cc1-4c4a3dfcc34d" />
<img width="1048" height="262" alt="image" src="https://github.com/user-attachments/assets/acf81cb1-4671-4964-b5b7-ea82b89993e0" />
D1SK3
-syntesizer - tool for conv rtl ->  netlist using (rtl,.lib -> yosys -> netlist)
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
to verify synthesis-

netlist + tb(sm as rtl tb) in  iverilog  gives vcd file which put into gtkwave gives u waveform which shud be same as observed using rtl syn
<img width="1115" height="645" alt="image" src="https://github.com/user-attachments/assets/f1d60174-9373-4dd7-9bff-952721cb5838" />

----------------------------------------------
RTL - behavioural representaion of rewuired specificatoin
result = netlist 
rtl- > gate level translation =  syn
.lib - collection of logical modules - and or nor nand and their diff flavours / specifications
combinational delay - maxm speed of ops 
tclk > tcq_a(prop d of ffa) + tcomb + tsetup_b
setup timr - minimum amount of time an input signal must remain stable before a triggering event
hold time-  The minimum amount of time a data signal must remain stable after a clock edge so a flip-flop can reliably capture it
FAST VS SLOW CELLS :-
<img width="818" height="512" alt="image" src="https://github.com/user-attachments/assets/d5249ac9-60c3-4ab0-9a62-2718d6bd81a9" />

------------------------------------------------------------------------------------------------------------
D1SK4
in verilog_files -> read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib  // to read standard lib into our design
<img width="815" height="607" alt="image" src="https://github.com/user-attachments/assets/2a2283dc-2a1d-4558-a95a-ab2620fef38f" />
<img width="911" height="417" alt="image" src="https://github.com/user-attachments/assets/0e36fb20-46e9-49ce-ac23-30f123b63520" />


read_verilog good_mux.v 
synth -top good_mux1
<img width="650" height="384" alt="image" src="https://github.com/user-attachments/assets/ed5684b7-61b4-4ea8-b843-8f19dc3f5027" />

 abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
 This command converts RTL code into gates,cells which is taken from the sky130_fd_sc_hd__tt_025C_1v80.lib file.
<img width="545" height="160" alt="image" src="https://github.com/user-attachments/assets/ed90d52f-e338-4482-9a1c-e29a2b4d1509" />
-liberty : It generate netlists for the specified cell library (using the liberty file format) and reintegrates mapping.

show
<img width="1919" height="804" alt="image" src="https://github.com/user-attachments/assets/6309bad2-7d6d-47dc-b8df-cf65898bee04" />

1st is 2 ip nand gate = ~(i1 & sel)
2nd is inverter = ~i0
3rd = o2ai or and invert gate  (sel| (~i0)) | ~(i1 & sel)
ans =  i1&sel | (~sel)&i0 

write_verilgo -noattr good_mux_netlist.v
-noattr- By using this option no attributes are included in the output. good_mux_netlist.v : File name to which we want to write the netlist.
check img
<img width="1919" height="804" alt="image" src="https://github.com/user-attachments/assets/f3c38af3-4f17-4cf8-b0cb-b2ec6b371a41" />
<img width="1282" height="810" alt="Screenshot 2026-05-27 221951" src="https://github.com/user-attachments/assets/77bbf9e3-ff5d-4a0d-a845-22a0c2dc377e" />
<img width="410" height="75" alt="image" src="https://github.com/user-attachments/assets/af29b9ba-e1db-420f-b04e-a278a1ab60b5" />






d2sk2

<img width="1039" height="378" alt="image" src="https://github.com/user-attachments/assets/bc06b449-26b9-40ba-8b15-c2ed0f905438" />

synth -top multiple_modules

<img width="509" height="802" alt="image" src="https://github.com/user-attachments/assets/4d94a3d8-7ee5-4b15-b9f8-c40a5b3d3439" />

<img width="719" height="504" alt="image" src="https://github.com/user-attachments/assets/3d46cdb8-dc6a-4c5d-8567-49e74af618ed" />

$abc -liberty file loc

now we $show filename but we get hierracrchial design

<img width="1497" height="805" alt="image" src="https://github.com/user-attachments/assets/79df9158-e2f6-461e-9f09-6888b8cff93e" /> 

no and or gates

<img width="525" height="161" alt="image" src="https://github.com/user-attachments/assets/719ff899-3378-4772-82da-e7aa608eb6c6" />

netlist dont forget -noattr

<img width="178" height="602" alt="image" src="https://github.com/user-attachments/assets/cd1d7469-fd0e-4ea0-bc9c-b6a462b34ced" />

to change this we use flatten

$flatten // command to wrute a flattened netlist

<img width="668" height="213" alt="image" src="https://github.com/user-attachments/assets/fdebe904-9b70-4f43-ac9f-5ac2edff7a42" />

<img width="650" height="130" alt="image" src="https://github.com/user-attachments/assets/bf90fb76-a1dd-45e9-9966-773c713d5aa5" />

Differnce b/w flat and hier - no sub modules in flat
 
<img width="1684" height="772" alt="image" src="https://github.com/user-attachments/assets/626e9c9f-57f5-4fcc-a7e5-33255e979f20" />

exit and again

<img width="828" height="297" alt="image" src="https://github.com/user-attachments/assets/d41c0860-5923-47a5-8f67-0ebf4640028b" />

$synth -top multiple_modules

<img width="513" height="334" alt="image" src="https://github.com/user-attachments/assets/3896e75d-0a83-454c-9e54-bde0115c0b11" />

<img width="528" height="536" alt="image" src="https://github.com/user-attachments/assets/c15be05d-4cc2-4973-9568-8f4525b6038c" />

<img width="520" height="392" alt="image" src="https://github.com/user-attachments/assets/76abb50e-1ab9-448d-b468-d0f43f91d01c" />

$abc -liberty loc

$flatten

<img width="644" height="228" alt="image" src="https://github.com/user-attachments/assets/e199b2c4-c482-4be9-ae6d-7a356c4667b8" />

$show 

<img width="1457" height="119" alt="image" src="https://github.com/user-attachments/assets/a9fc8488-bf9e-46c2-9411-340ede4a3a97" /> 

now we see and , or inverrter gates

we see full structure after flattening

now lets do for a submodule

$read_liberty -lib path

$read_verilog file

$synth -top submod //imp

$abc -liberty path

$show

<img width="1695" height="893" alt="image" src="https://github.com/user-attachments/assets/ed48514c-9be9-4534-90ea-7cc5fadc1917" />

Why do we do this ? - if u have the same module multiple times it would be a waste to synthesise all so we just synthesize one and then stitch it together in top

Difference between hierarchial and flattened

Hierarchial -Only modules level , Faster , preserved hierarchy,Modular structure 

Flattened -whole design shown,slower,Collapsed hierarchy,Single, complex netlist

-----------------------------------------------------------------------------------------------------------------------------------------------------
Flip flops
----------

D Flip flop 's asyncronous reset / set 

- if any one of asyncreset or asyncset triggered u enter the always

- clk has no use cause reset/set asynchronous here

-an always block runs continuously but only executes the code inside it when triggered by a specific event defined in its sensitivity list

Asynchronous

```verilog
module dff_asyncres(input clk , d,asyncreset , output reg q);
always @(posedge clk  , posedge asyncreset)
begin
 if(asyncreset)begin //for set sm code but change mod name ,asyncreset -> asyncset , q<=1'b1
 q <= 1'b0;
 else
 q<=d;
end
endmodule
```

Synchronous

'''verilog
module dff_syncres(input clk ,asyncreset, d,syncreset , output reg q);
always @(posedge clk ) //only triggered on clk edge not based on values of syncreset
begin
 if(syncreset)begin //for set sm code but change mod name ,asyncreset -> asyncset , q<=1'b1
 q <= 1'b0; 
 else
 q<=d;
end
endmodule
'''

<img width="824" height="690" alt="image" src="https://github.com/user-attachments/assets/e25f9bc7-34f5-45e9-93da-a3876b3c93eb" />

If entered on asyncreset -> q <= 0

If entered on clk pulse -> if syncreset = 1 -> q<=0

Else q<=d

----------------------------------------

To use iverilog :-

In verilog_files :- 
$iverilog dff_asyncres.v tb_dff_asyncres.v //compile

$./a.out    //run

<img width="927" height="150" alt="image" src="https://github.com/user-attachments/assets/b379e893-588e-41e8-b982-98ead2695af2" />

$gtkwave tb_dff_asyncres.vcd //view waveform

<img width="1120" height="706" alt="image" src="https://github.com/user-attachments/assets/d7fab6cd-2deb-42f2-9520-9ac70d97ffc8" />

<img width="1131" height="700" alt="image" src="https://github.com/user-attachments/assets/078e13ee-a422-4c63-b827-5c7458746bfc" />

<img width="1140" height="702" alt="image" src="https://github.com/user-attachments/assets/b1bc96cf-efda-472d-bf64-a5b629c5a81d" />

using yosys to synthesize

<img width="806" height="237" alt="image" src="https://github.com/user-attachments/assets/696285eb-db2e-4dda-81ea-5f051d71ae29" />

since were using dffs keyword - dfflibmap

$abc -liberty fileloc

$show

<img width="1051" height="163" alt="image" src="https://github.com/user-attachments/assets/3e7514eb-74f4-4f27-a16a-40b19c2cd700" />

lib had active low set so inv used

sync_res->

<img width="1427" height="272" alt="image" src="https://github.com/user-attachments/assets/4707627a-5eae-4768-8aef-78e33fd4c44b" />

-----------------------------------------
OPTIMIZATION
-------------

Here ,we use 2 files mul2 and mul9.

```verilog
module mul2(input [2:0] a , output [3:0] y);
assign y = a * 2 ; //basically a left shift a<<1 
endmodule
```

<img width="499" height="278" alt="image" src="https://github.com/user-attachments/assets/cc89d5b1-3c4a-4cdd-9b0c-5147954c9900" />

no cells used 

when we call abc -liberty 

<img width="902" height="186" alt="image" src="https://github.com/user-attachments/assets/551fb070-acda-4996-8d82-3020d37af775" />

$show

<img width="433" height="209" alt="image" src="https://github.com/user-attachments/assets/ebc1a2b2-4dce-4ac2-83f4-775f9b503f4e" />

what happens

y[3:1] = a[2:0]    (a's bits shifted left by 1)

y[0]   = 1'b0      (LSB forced to 0)

$write_verilog -noattr mul2_net.v 

<img width="606" height="155" alt="image" src="https://github.com/user-attachments/assets/7d1a3fb8-5efe-4d54-86ee-f387f9c11e17" />
















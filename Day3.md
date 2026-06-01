Intro to Logic Optimization
1. Constant Logic Optmi

2. Boolean Logic Optim - basically kmap
-----------------------------------------------
Sequential LOgic op
seque constant prop - for it to be used q pin shud have constant value.
<img width="1186" height="648" alt="image" src="https://github.com/user-attachments/assets/200eb0be-9633-4f6c-9af6-36310ac9a88f" />
Theoratical Concepts (no labs)
1.State OPtimization - optmz of unused states
2. Cloning
3. Retiming

Labs
1.opt_check.v

```verilog
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```
<img width="787" height="250" alt="image" src="https://github.com/user-attachments/assets/e044fd41-d10f-4269-98d5-1d88bb82ca8f" />
<img width="721" height="375" alt="image" src="https://github.com/user-attachments/assets/c81cc32a-9407-43c4-a0a7-9e0a8e825df4" />
$opt_clean -purge
<img width="683" height="110" alt="image" src="https://github.com/user-attachments/assets/4630a11a-0473-46fb-aeb9-db9e3ee436a7" />
do abc -liberty and show
<img width="687" height="144" alt="image" src="https://github.com/user-attachments/assets/9d4bc666-c908-4857-9d80-10a01d5fd774" />
This is basically an AND gate.

optcheck2.v

```verilog
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```
<img width="668" height="387" alt="image" src="https://github.com/user-attachments/assets/c123504b-a3a3-4bfb-a5f2-4ec1bcf9c464" />
do synth,opt_clean -purge , abc -liberty file_loc , show
<img width="711" height="161" alt="image" src="https://github.com/user-attachments/assets/34620c7f-fd83-44c9-b67c-3e50d3a27599" />

optcheck3.v

```verilog
module opt_check3(input a , input b, output y);
	assign y = a?(c?b:0):0 ;
endmodule
```
this gives u a&b&c 
<img width="769" height="288" alt="image" src="https://github.com/user-attachments/assets/a9f55258-d912-4d6a-9728-63a099ad2b20" />
<img width="675" height="214" alt="image" src="https://github.com/user-attachments/assets/43830753-8b7e-4fd0-bd0c-fafd35acb47a" />

opt_check4.v

```verilog
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
 endmodule
```
simplifies to a xnor gate 
y = ac + a'c'

<img width="667" height="382" alt="image" src="https://github.com/user-attachments/assets/f792a57d-aa56-49c7-b54c-cdd163f9e773" />
<img width="754" height="223" alt="image" src="https://github.com/user-attachments/assets/421c5140-2ac2-4f34-8f81-afcf214aecba" />

///multiple modules left

-----------------------------------------------------------------------------------------------
ffs
<img width="508" height="171" alt="image" src="https://github.com/user-attachments/assets/d5adffbe-c12a-489b-9171-20c766f67a8b" />

```verilog
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```
<img width="1143" height="697" alt="image" src="https://github.com/user-attachments/assets/bdf9c852-055b-480f-8589-63445ef09969" />
dfflibmap after synth
<img width="925" height="49" alt="image" src="https://github.com/user-attachments/assets/592545fc-97d3-4024-9f78-cec9e5482d29" />
abc -liberty
<img width="676" height="146" alt="image" src="https://github.com/user-attachments/assets/48ed1058-132e-43d8-9c4c-7ae6b74382b6" />



ff2
```verilog
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```
basically always 1

<img width="1161" height="714" alt="image" src="https://github.com/user-attachments/assets/49ef05ef-2ccc-4a25-86c3-5e92ea4223c8" />
<img width="684" height="425" alt="image" src="https://github.com/user-attachments/assets/0ec48592-5a2e-4e5a-bc92-68e595cad8d7" />

dff_const3.v
<img width="1445" height="793" alt="image" src="https://github.com/user-attachments/assets/d1dabbdc-29c1-4e52-975e-d2ce800323a1" />
yosys
<img width="679" height="416" alt="image" src="https://github.com/user-attachments/assets/41e133ac-e399-4eae-938d-a3915ffd383c" />

<img width="1427" height="255" alt="image" src="https://github.com/user-attachments/assets/0b5734a9-f1eb-41a0-8598-913914ef64a5" />
//do const4 and 5
dff_const4.v
<img width="461" height="256" alt="image" src="https://github.com/user-attachments/assets/a6e4e855-5214-4d27-8fac-5efd0ae654d6" />

<img width="668" height="573" alt="image" src="https://github.com/user-attachments/assets/303f8db4-553d-415e-bdc7-9798fcbee98b" />

dff_const5.v

<img width="512" height="248" alt="image" src="https://github.com/user-attachments/assets/a1cf90c7-c820-4ca6-bb60-238bdae9932e" />
<img width="1444" height="268" alt="image" src="https://github.com/user-attachments/assets/969a1b18-fbd6-4102-9c53-e42fb0a7ae85" />




-------------------------------------------------------------------
unused output optm
counter
```verilog

module counter_opt (input clk , input reset , output q);
  reg [2:0] count;
  assign q =(count[0]==3'b110);

  always @(posedge clk ,posedge reset)
  begin
   if(reset)
   	count <= 3'b000;
   else
   	count <= count + 1;
  end

 endmodule
 ```
<img width="673" height="421" alt="image" src="https://github.com/user-attachments/assets/2b3cc7fa-1c11-46ce-93da-740f82ff3e6f" />
<img width="1444" height="157" alt="image" src="https://github.com/user-attachments/assets/fa5c2253-5f33-4e3a-8569-6d7b371adf50" />





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
<img width="668" height="387" alt="image" src="https://github.com/user-attachments/assets/c123504b-a3a3-4bfb-a5f2-4ec1bcf9c464" />
do synth,opt_clean -purge , abc -liberty file_loc , show
<img width="711" height="161" alt="image" src="https://github.com/user-attachments/assets/34620c7f-fd83-44c9-b67c-3e50d3a27599" />



d2sk2
<img width="1039" height="378" alt="image" src="https://github.com/user-attachments/assets/bc06b449-26b9-40ba-8b15-c2ed0f905438" />
synth -top multiple_modules
<img width="509" height="802" alt="image" src="https://github.com/user-attachments/assets/4d94a3d8-7ee5-4b15-b9f8-c40a5b3d3439" />
<img width="719" height="504" alt="image" src="https://github.com/user-attachments/assets/3d46cdb8-dc6a-4c5d-8567-49e74af618ed" />
abc -liberty file loc
now we $show filename but we get hierracrchial design
<img width="1497" height="805" alt="image" src="https://github.com/user-attachments/assets/79df9158-e2f6-461e-9f09-6888b8cff93e" /> //no and or gates
<img width="525" height="161" alt="image" src="https://github.com/user-attachments/assets/719ff899-3378-4772-82da-e7aa608eb6c6" />
netlist dont forget -noattr
<img width="178" height="602" alt="image" src="https://github.com/user-attachments/assets/cd1d7469-fd0e-4ea0-bc9c-b6a462b34ced" />
to change this we use flatten
flatten - command to wrute a flattened netlist
<img width="668" height="213" alt="image" src="https://github.com/user-attachments/assets/fdebe904-9b70-4f43-ac9f-5ac2edff7a42" />

<img width="650" height="130" alt="image" src="https://github.com/user-attachments/assets/bf90fb76-a1dd-45e9-9966-773c713d5aa5" />
 diff b/w flat and hier
 - no sub modules in flat
 <img width="1684" height="772" alt="image" src="https://github.com/user-attachments/assets/626e9c9f-57f5-4fcc-a7e5-33255e979f20" />

exit and again
<img width="828" height="297" alt="image" src="https://github.com/user-attachments/assets/d41c0860-5923-47a5-8f67-0ebf4640028b" />
synth -top multiple_modules
<img width="513" height="334" alt="image" src="https://github.com/user-attachments/assets/3896e75d-0a83-454c-9e54-bde0115c0b11" />
<img width="528" height="536" alt="image" src="https://github.com/user-attachments/assets/c15be05d-4cc2-4973-9568-8f4525b6038c" />

<img width="520" height="392" alt="image" src="https://github.com/user-attachments/assets/76abb50e-1ab9-448d-b468-d0f43f91d01c" />

abc -liberty
flatten
<img width="644" height="228" alt="image" src="https://github.com/user-attachments/assets/e199b2c4-c482-4be9-ae6d-7a356c4667b8" />

show 
<img width="1457" height="119" alt="image" src="https://github.com/user-attachments/assets/a9fc8488-bf9e-46c2-9411-340ede4a3a97" /> now we see and , or inverrter gates
we see full structure after flattening

now lets do for a submodule
$read_liberty -lib path
$read_verilog file
$synth -top submod //imp
$abc -liberty path
$show

<img width="1695" height="893" alt="image" src="https://github.com/user-attachments/assets/ed48514c-9be9-4534-90ea-7cc5fadc1917" />
why do we do this ? - if u have the same module multiple times it would be a waste to synthesise all so we just synthesize one and then sitch it together in top
Difference between hierarchial and flattened
H-Only modules level , Faster , preserved hierarchy,Modular structure 
Flattened-whole design shown,slower,Collapsed hierarchy,Single, complex netlist

flip flops --



----

```module dff_asyncres(input clk , d,asyncreset , output reg q);
always @(posedge clk  , posedge asyncreset)
begin
 if(asyncreset)begin
 q <= 1'b0;
 else
 q<=d;
 
 

end
endmodule
```





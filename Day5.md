1.If else : used for conditional execution in behavioral modeling, typically within procedural blocks (always, initial, tasks, or functions).
```verilog
    if (condition1) begin
    // Code for condition1 
        end
    else if (condition2) begin
    // Code for condition2 true
    end
    else begin
    // Code if no conditions are true
    end
```

2.Inferred latches occur when a combinational logic block does not assign a value to a variable in all possible execution paths.
This causes the synthesis tool to infer a latch, which may not be the designer’s intention.
This may cause timing errors and racearound conditions.
In this case u can either use case - endcase (reg can be used) (remember to put a fefsult to prevent racearound) or add an else .

 PRIOPRITY

--------------
D5SK2 
Lab1:
```verilog
module incomp_if (input i0, input i1, input i2, output reg y);
always @(*) begin
    if (i0)
        y <= i1;
end
endmodule
```

<img width="1432" height="805" alt="image" src="https://github.com/user-attachments/assets/4d5d74cd-121a-41a4-a400-b72456735689" />

<img width="677" height="306" alt="image" src="https://github.com/user-attachments/assets/34d39cfe-5e24-4f0a-ab26-a8cbda1d5c83" />

<img width="310" height="205" alt="image" src="https://github.com/user-attachments/assets/470d40df-239d-4804-a962-9f987e761035" />

 Lab2:
 ```verilog
module incomp_if2 (input i0, input i1, input i2, input i3, output reg y);
always @(*) begin
    if (i0)
        y <= i1;
    else if (i2)
        y <= i3;
end
endmodule
```
<img width="551" height="305" alt="image" src="https://github.com/user-attachments/assets/aab51ffd-f760-4cf8-894f-79b401086db0" />

<img width="1459" height="746" alt="image" src="https://github.com/user-attachments/assets/11557ece-afa5-422e-acb7-0192db0f2985" />

<img width="1443" height="330" alt="image" src="https://github.com/user-attachments/assets/d4660627-4fd3-4f57-8384-3ca52e8725ef" />

D5SK3
Lab1:

```verilog

module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
case(sel)
	2'b00 : y = i0;
	2'b01 : y = i1;
endcase
end
endmodule
```

<img width="1137" height="579" alt="Screenshot 2026-06-01 015733" src="https://github.com/user-attachments/assets/8849b46f-a059-4574-b212-c03d7781b4d8" />

<img width="689" height="478" alt="Screenshot 2026-06-01 015832" src="https://github.com/user-attachments/assets/bec29dad-2c2f-424d-8a06-019888d86788" />

<img width="710" height="176" alt="Screenshot 2026-06-01 015852" src="https://github.com/user-attachments/assets/b9abe854-e96f-49ac-8dec-a91af663260f" />

<img width="1475" height="253" alt="Screenshot 2026-06-01 015908" src="https://github.com/user-attachments/assets/2de62181-c661-49fc-9489-457179fdffcb" />

<img width="788" height="325" alt="Screenshot 2026-06-01 020128" src="https://github.com/user-attachments/assets/26d4faa6-a8e5-4065-8b75-aaacf03d46a6" />

Lab 2:

```verilog
module comp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
  always @ (*)
   begin
  case(sel)
  	2'b00 : y = i0;
  	2'b01 : y = i1;
  	default : y = i2;
  endcase
   end
   endmodule
```
<img width="444" height="261" alt="image" src="https://github.com/user-attachments/assets/5568139b-7524-42cb-bc21-661a2dd9c188" />

<img width="1126" height="552" alt="image" src="https://github.com/user-attachments/assets/e3889f4e-4936-408e-9cd8-ce9757ccfeb5" />

<img width="553" height="369" alt="image" src="https://github.com/user-attachments/assets/a3ec4971-f55d-41cf-9f0d-e93699a56321" />

<img width="745" height="195" alt="image" src="https://github.com/user-attachments/assets/082f8e97-33bd-48a9-aa21-6576ec403c25" />

<img width="1447" height="311" alt="image" src="https://github.com/user-attachments/assets/88cced3d-c7ff-4b22-8ea8-9595a9a108bd" />

Lab3:partial_case_asign

<img width="671" height="472" alt="image" src="https://github.com/user-attachments/assets/cc34f8ba-0fd9-43b3-a2c1-8e413d5420e2" />

<img width="682" height="232" alt="image" src="https://github.com/user-attachments/assets/2b7d079e-2f23-4e42-a086-f4f0bb9d77e7" />

<img width="1421" height="428" alt="image" src="https://github.com/user-attachments/assets/1de2b965-330a-4113-8f30-8a39af55e3a9" />
<img width="559" height="317" alt="image" src="https://github.com/user-attachments/assets/894f4e7a-d4c3-4d9e-983d-b8b801e7249b" />
en = sel1 + sel0'

Looping Concepts
1. For Loop
-used in always
-evaluating expresion

2.Generate For Loop
-used outside always
-instantiating hardware eg. if u want u instantiate an or / and gate multiple times

```verilog
integer i;
always @(*) begin
    for (i = 0; i < 32; i = i + 1) begin
        if (select == i[4:0])
            data_out = data_in[i];
    end
end
```
----------------------------------------

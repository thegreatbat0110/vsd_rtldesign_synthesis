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

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

Differences between case and if-else :-

<img width="735" height="455" alt="image" src="https://github.com/user-attachments/assets/69f4093d-3ca9-4687-bee7-71b3685140a9" />

---------------------------------------------------------------
D5SK2
------

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
-----

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
------

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

Lab2:

```verilog
module partial_case_assign (
    input i0, input i1, input i2,
    input [1:0] sel,
    output reg y, output reg x
);
always @(*) begin
    case(sel)
        2'b00: begin
            y = i0;
            x = i2;
        end
        2'b01: y = i1;
        default: begin
            x = i1;
            y = i2;
        end
    endcase
end
endmodule
```

<img width="663" height="477" alt="image" src="https://github.com/user-attachments/assets/8d82c2df-3ccc-4e3c-be7a-4752ad2975fc" />

<img width="681" height="226" alt="image" src="https://github.com/user-attachments/assets/e0ee1765-f4a9-4069-8223-b76761df16b6" />

<img width="1448" height="448" alt="image" src="https://github.com/user-attachments/assets/f4b0ae8a-539a-4280-8fef-4c1175d7b5b5" />

Lab3:

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

partial_case_asign   //done double remove

<img width="671" height="472" alt="image" src="https://github.com/user-attachments/assets/cc34f8ba-0fd9-43b3-a2c1-8e413d5420e2" />

<img width="682" height="232" alt="image" src="https://github.com/user-attachments/assets/2b7d079e-2f23-4e42-a086-f4f0bb9d77e7" />

<img width="1421" height="428" alt="image" src="https://github.com/user-attachments/assets/1de2b965-330a-4113-8f30-8a39af55e3a9" />

<img width="559" height="317" alt="image" src="https://github.com/user-attachments/assets/894f4e7a-d4c3-4d9e-983d-b8b801e7249b" />

en = sel1 + sel0'

Lab4: 

bad_case.v

```verilog
module bad_case (
    input i0, input i1, input i2, input i3,
    input [1:0] sel,
    output reg y
);
always @(*) begin
    case(sel)
        2'b00: y = i0;
        2'b01: y = i1;
        2'b10: y = i2;
        2'b1?: y = i3; // be careful with incomplete cases , tool gets confused
    endcase
end
endmodule
```

<img width="1130" height="677" alt="image" src="https://github.com/user-attachments/assets/899c64fe-62b4-401f-bc6c-52a5525fad12" />

<img width="693" height="448" alt="image" src="https://github.com/user-attachments/assets/ca4cb6e6-d482-4bdd-921d-75517d295e9d" />

<img width="612" height="146" alt="image" src="https://github.com/user-attachments/assets/c19e829e-826b-44a8-87dc-e39f50a3f63c" />

<img width="1461" height="757" alt="image" src="https://github.com/user-attachments/assets/fadc1ad8-92b6-4fc3-bdef-4ee67bbd8786" />

<img width="1128" height="710" alt="image" src="https://github.com/user-attachments/assets/d5488699-14ea-4e14-9de5-b97e7e8e55c5" />

Note the xx

<img width="838" height="271" alt="image" src="https://github.com/user-attachments/assets/1aaeb5af-37ca-4c23-a082-631e19bb047d" />

---------------------------------------------------------------------------------------------------------------

Looping Concepts
----------------

1. For Loop
-used in always
-evaluating expresion

2.Generate For Loop
-used outside always
-instantiating hardware eg. if u want u instantiate an or / and gate multiple times

MUX
```verilog
integer i;
always @(*) begin
    for (i = 0; i < 32; i = i + 1) begin
        if (select == i[4:0])
            data_out = data_in[i];
    end
end
```

DEMUX
```verilog
integer m;
always @(*) begin
data_out[7:0] = 8'b0 ;
for (m = 0;m<8;m=m+1)begin
if(m == sel)begin
	data_out[m] = data_in ;
end
end
end
```

Genvar is a special keyword used to declare a generation loop variable. It acts as an iterator exclusively during the elaboration phase (compile/build time) to duplicate hardware structures programmatically. It does not represent a physical register or wire, and it entirely disappears before simulation or runtime begins

GENERATE FOR

```verilog

genvar i;
generate
for (m = 0;m<8;m=m+1)begin
	and u_ans(.a(in1[i]),.b(in2[i]),.y(y[i]));
endgenerate
end
``` 
----------------------------------------

Lab1:
```verilog
module mux_generate (
    input i0, input i1, input i2, input i3,
    input [1:0] sel,
    output reg y
);
wire [3:0] i_int;
assign i_int = {i3, i2, i1, i0};
integer k;
always @(*) begin
    for (k = 0; k < 4; k = k + 1) begin
        if (k == sel)
            y = i_int[k];
    end
end
endmodule
```

<img width="1312" height="713" alt="image" src="https://github.com/user-attachments/assets/e0ee6229-8297-43f9-bd4d-95a8a6de00ab" />

<img width="652" height="167" alt="image" src="https://github.com/user-attachments/assets/203ee52c-8cd0-4c23-b97a-c5fd936a7573" />

<img width="681" height="433" alt="image" src="https://github.com/user-attachments/assets/846d03af-d74e-42c9-9463-4fd50f5047b7" />

Lab2: 
1.Mux using case

```verilog
module demux_case (
    output o0, output o1, output o2, output o3,
    output o4, output o5, output o6, output o7,
    input [2:0] sel,
    input i
);
reg [7:0] y_int;
assign {o7, o6, o5, o4, o3, o2, o1, o0} = y_int;
always @(*) begin
    y_int = 8'b0;
    case(sel)
        3'b000 : y_int[0] = i;
        3'b001 : y_int[1] = i;
        3'b010 : y_int[2] = i;
        3'b011 : y_int[3] = i;
        3'b100 : y_int[4] = i;
        3'b101 : y_int[5] = i;
        3'b110 : y_int[6] = i;
        3'b111 : y_int[7] = i;
    endcase
end
endmodule
```

<img width="460" height="400" alt="image" src="https://github.com/user-attachments/assets/1e51363e-e69b-49e6-9496-66821417d966" />

<img width="669" height="213" alt="image" src="https://github.com/user-attachments/assets/a94bdcd8-4636-4e57-9d3b-09cffa767ca4" />

<img width="663" height="723" alt="image" src="https://github.com/user-attachments/assets/feed51b4-8c97-4ad8-b2cb-e10c082c7650" />

<img width="1104" height="697" alt="image" src="https://github.com/user-attachments/assets/f65b02f6-3a34-412f-b563-2a8216314915" />

<img width="835" height="547" alt="image" src="https://github.com/user-attachments/assets/2432bc51-0d77-4bfc-954c-8faf8325ba6c" />

<img width="862" height="593" alt="image" src="https://github.com/user-attachments/assets/fbb03ae2-4e3f-4762-961f-5ebd3241e285" />

2.Using Loop:

```verilog
module demux_generate (
    output o0, output o1, output o2, output o3,
    output o4, output o5, output o6, output o7,
    input [2:0] sel,
    input i
);
reg [7:0] y_int;
assign {o7, o6, o5, o4, o3, o2, o1, o0} = y_int;
integer k;
always @(*) begin
    y_int = 8'b0;
    for (k = 0; k < 8; k = k + 1) begin
        if (k == sel)
            y_int[k] = i;
    end
end
endmodule
```

<img width="687" height="601" alt="image" src="https://github.com/user-attachments/assets/97359321-7512-4175-bf61-6a8d20dea401" />

<img width="819" height="563" alt="image" src="https://github.com/user-attachments/assets/b207b459-6333-483f-8d11-20ee73bf0f28" />

<img width="865" height="589" alt="image" src="https://github.com/user-attachments/assets/5296cd8e-c636-4e8d-99a7-cafcc40e6210" />

Lab3:

```verilog
module rca (
    input [7:0] num1,
    input [7:0] num2,
    output [8:0] sum
);
wire [7:0] int_sum;
wire [7:0] int_co;

genvar i;
generate
    for (i = 1; i < 8; i = i + 1) begin
        fa u_fa_1 (.a(num1[i]), .b(num2[i]), .c(int_co[i-1]), .co(int_co[i]), .sum(int_sum[i]));
    end
endgenerate

fa u_fa_0 (.a(num1[0]), .b(num2[0]), .c(1'b0), .co(int_co[0]), .sum(int_sum[0]));

assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule
```

<img width="1364" height="189" alt="image" src="https://github.com/user-attachments/assets/89860c29-c223-4166-8439-15bb38532031" />

<img width="1378" height="175" alt="image" src="https://github.com/user-attachments/assets/9844c8ff-55a7-4e3a-8a1e-e9fc5ee0ab4f" />

<img width="1361" height="179" alt="image" src="https://github.com/user-attachments/assets/b80b6438-56a6-4418-b2b4-6bda4ad8a1c6" />

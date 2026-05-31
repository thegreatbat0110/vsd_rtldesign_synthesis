Lab 1:
```verilog
module ternary_operator_mux (input i0, input i1, input sel, output y);
  assign y = sel ? i1 : i0;
endmodule
```
<img width="1412" height="638" alt="image" src="https://github.com/user-attachments/assets/621839dd-16fb-4254-9402-85586991fbdb" />
<img width="693" height="204" alt="image" src="https://github.com/user-attachments/assets/472b9a24-64a6-4261-a7da-c80d8b25bd25" />
using write_verilog after abc -lib
<img width="706" height="307" alt="image" src="https://github.com/user-attachments/assets/44880e1d-bbd2-451d-b934-9301219e99b2" />
take noteof teh commands
<img width="1458" height="774" alt="image" src="https://github.com/user-attachments/assets/1b4ce72c-5043-401a-8275-1fc871979be3" />
<img width="1002" height="699" alt="image" src="https://github.com/user-attachments/assets/19c8a485-df9c-41c9-b3d5-d676d014993a" />

------------------------------------------------------------------------------------------------------------------------------------

Lab2:
bad_mux.v
here only sel is in sensitivity list so error
<img width="1218" height="139" alt="image" src="https://github.com/user-attachments/assets/a8eda6d0-f932-45ed-9c5c-4f5a3132a07e" />
Synthesis Simulation mismatch due to missing sensitivity list

A synthesis-simulation mismatch occurs when the simulation results of RTL (pre-synthesis) do not match simulation results of the gate-level netlist (post-synthesis) or hardware. Reasons include:

Non-synthesizable constructs: Use of delays, initial blocks, or other code not supported by synthesis.
Incomplete or ambiguous coding: E.g., missing else clauses, improper sensitivity lists.
Tool interpretation differences: Simulation and synthesis tools may interpret ambiguous RTL differently.

Key Point: Always write synthesizable, unambiguous RTL and follow good coding practices to minimize mismatches.

 <img width="1152" height="510" alt="image" src="https://github.com/user-attachments/assets/cfbb6821-5a4f-4e44-ab2d-644d9065c87f" />

<img width="488" height="318" alt="image" src="https://github.com/user-attachments/assets/53f92e14-174b-4f49-ae24-16899c09cdfe" />
<img width="697" height="196" alt="image" src="https://github.com/user-attachments/assets/26ab4113-1303-4f8d-91a4-1586cde3a511" />

<img width="1136" height="694" alt="image" src="https://github.com/user-attachments/assets/764a42db-b416-4bf7-b63b-2fba4294e00f" />

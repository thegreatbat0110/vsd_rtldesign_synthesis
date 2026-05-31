1. If else : used for conditional execution in behavioral modeling, typically within procedural blocks (always, initial, tasks, or functions).
    ```verilog
    if (condition1) begin
    // Code for condition1 true
end else if (condition2) begin
    // Code for condition2 true
end else begin
    // Code if no conditions are true
end
```
2. Inferred latches occur when a combinational logic block does not assign a value to a variable in all possible execution paths.
This causes the synthesis tool to infer a latch, which may not be the designer’s intention.
This may cause timing errors and racearound conditions.
In this case u can either use case - endcase (reg can be used) (remember to put a fefsult to prevent racearound) or add an else .

!! PRIOPRITY
--------------

For Loop

Lab 1 :

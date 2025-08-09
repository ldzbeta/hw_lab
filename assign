Here’s the styled Markdown version of your Verilog explanation:

---

### When to Use `always` in Verilog

You use an `always` block in Verilog when:

1. **Describing Procedural Logic**  
   - Use `if`, `case`, `for`, or `while` constructs inside the block.
   - Assign values to `reg` types within the block.

2. **Modeling Logic Types**  
   - **Combinational Logic**:  
     ```verilog
     always @(*) begin
         if (sel)
             y = a & b;
         else
             y = a | b;
     end
     ```
     - Executes whenever any input changes (`@(*)`).

   - **Sequential Logic**:  
     ```verilog
     always @(posedge clk) begin
         q <= d;
     end
     ```
     - Executes on clock edges (`posedge clk`).

3. **Priority or Default Behaviors**  
   - Use when logic isn’t easily expressible with `assign`.

---

### When **Not** to Use `always`

- The logic can be written as a direct equation with `assign`.
- The logic involves pure Boolean expressions without control flow.

--- 

Let me know if you'd like any further refinements!

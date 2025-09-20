# 🔹 Asynchronous Active-Low Reset

-Asynchronous reset means:  
The flip-flop output resets immediately when reset is asserted, regardless of the clock.  
It does not wait for a clock edge.

-Active-low means:  
The reset signal works when it is logic 0.  
(So reset = 0 → clear outputs, reset = 1 → normal operation.)

In Verilog, this is modeled with:

```verilog
always @(posedge clk or negedge rst_n) begin
    if (!rst_n) 
        q <= 0;       // reset active when rst_n = 0
    else 
        q <= d;       // normal flop operation
end
```

📌 Example: If rst_n=0, the register is cleared instantly, without waiting for posedge clk.

# 🔹 Alternatives

There are two main reset styles:

## Asynchronous Active-High Reset
Reset works when reset = 1.  
Triggered immediately, not waiting for clock.

```verilog
always @(posedge clk or posedge reset) begin
    if (reset)
        q <= 0;
    else
        q <= d;
end
```

## Synchronous Reset (Active-High or Active-Low)
Reset is checked only at the active clock edge.

Example (synchronous active-high):

```verilog
always @(posedge clk) begin
    if (reset)
        q <= 0;     // reset only at clk edge
    else
        q <= d;
end
```

Example (synchronous active-low):

```verilog
always @(posedge clk) begin
    if (!rst_n)
        q <= 0;
    else
        q <= d;
end
```

# 🔹 Comparison

| Reset Type            | Works When       | Needs Clock? | Common Use                                   |
|-----------------------|------------------|--------------|----------------------------------------------|
| **Async Active-Low**  | reset = 0        | ❌ No        | Most FPGA libraries, safer at power-up       |
| **Async Active-High** | reset = 1        | ❌ No        | Sometimes in ASICs                            |
| **Sync Active-High**  | reset = 1 on clk | ✅ Yes       | Control-heavy designs                        |
| **Sync Active-Low**   | reset = 0 on clk | ✅ Yes       | Less common                                  |

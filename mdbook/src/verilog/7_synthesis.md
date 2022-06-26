
## Specifying Registers in verilog

- initial block in not synthesizable
- posedge will result in flip flop
- use non-blocking for sequential 

![image]()

- only use reg within procedural block
- if the logic is sequential then only the clock will be in sensitivity list
- because the logic is synchronous everything will be in control of clock- clock is edge sensitive and reset is level sensitive
- hardware depends on coding style not the data type

- Asynchronous reset = `posedge clock or posedge reset`
- Synchronous reset = `posedge clock`

[unwanted latch]()

- use default assignment for avoiding unwanted latches
- Always use default case statement
- Assign every output in every branch
- Use default assignments

## Synthesis of Operators

- Nearly all of the Verilog operators are Synthesizable, however there are a few issues to bear in mind when using them.
- Some synthesis tools can choose macro-cells automatically
- Some synthesis tools will allow you to specify what architecture should be used

## Resource Sharing

- Some synthesis tools can perform this optimization automatically
- If the synthesis tool cannot perform this optimization, the Verilog code can be re-written to achieve the same result
- Use parentheses to optimize logic structure
- if else if - infers priority encoded "cascading" mux’s in your design
- Case — infers "tall and skinny" mux’s in your design with no priority


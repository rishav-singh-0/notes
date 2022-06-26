# Verilog - Assignments

## Types of assignments

### Continuous assignments

- Assigns values to nets
- This assignment occurs whenever the value of the right-hand side changes
- Executes in parallel
- Continuously active
- Order independent
- LHS must be wire data type, RHS could be reg or wire

```
wire c, a, b;
assign #2 c = a & b;
```
- Here, RHS will be computed after 2 time unit delay, then result will be assigned to LHS

### Procedural assignments

- Update the value of variables under the control of the procedural flow constructs that surround them
- Each procedure represents a separate activity flow in Verilog, all of which run in parallel
- For multiple parallel procedural blocks order of execution is indeterministic.
- LHS must be reg datatype

#### initial Block
- Execution starts at zero simulation time
- Once executable only
- Only for testbench not for rtl

#### always Block
- Repeats continuously throughout the duration of the simulation
- If an always construct has no control for simulation time to advance, it will create a simulation deadlock condition

## Event Controls

- Event - a change in value on a register or net.
- A posedge is detected on the transition from 0 to x, z, or 1, and from x or z to 1
- A negedge is detected on the transition from 1 to x, z, or 0, and from x or z to 0
```
always @ (triggering_signal)
  begin
    ......
  end
```

## Sensitivity List
- Without sensitivity list ,the always block will loop continuously without waiting for a triggering event.
- All net and variable identifiers which appear in the statement will be automatically added to the event expression

```
  module ev_exp_check (a, b, c, d, f, y);
  input [1:0] a, b, c, d, f;
  output y;
  reg [1:0] y;

  // equivalent to @(a or b or c or d or f)
  always @(*)
    y = (a & b) | (c & d) | f;
  endmodule
```

## Level-sensitive event control
wait_statement

- It is a special form of event control. The nature of the wait statement is level-sensitive

- wait statement evaluates a condition, and, if it is false, the procedural statements following the wait statement remains blocked until that condition becomes true

- Only for testbench

```
begin
  wait (!enable)
  #10 a = b;
  #10 c = d;
end
```

## Procedural Assignment Delays

### Regular Delay

- When the delay is specified on the LHS of the procedural assignment, it means that this is the delay before the RHS is evaluated and assigned to the LHS.
```
#5 b = 1'b1;
```

### Intra-assignment Delay

- The RHS of the equation is evaluated at the current time but the assignment is not made until after the delay time
- intra-assignment delay can be applied to both blocking assignments and non blocking assignments

```
a = #10 b;
```

## Block statements

- The block statements are a means of grouping two or more statements together so that they act syntactically like a single statement.

- Two Types :
  - Sequential block, also called begin-end block
  - Parallel block, also called fork-join block

- Both sequential and parallel blocks can be named by adding : name_of_block after the keywords begin or fork.

### Sequential Block (begin - end block)

- Statements executes in sequence, one after another
- Delay values for each statement is treated relative to the simulation time of the execution of the previous statement
- Control is passed out of the block after the last statement executes
- Final delay will be addition of all delays

```
initial
  begin
    .....
  end
```

### Parallel Block (fork - join block)

- Statements executes concurrently
- Delay values for each statement is considered relative to the simulation time of entering the block
- Delay control can be used to provide time-ordering for assignments
- Control is passed out of the block when the last time-ordered statement executes
- Final delay will be maximum of all delays

```
initial
  fork
    .....
  join
```

## Event timing controls

- Not for synthesis
- `@(posedge clock) a = b;` - event control with regular delay
- `a = @(posedge clock) b;` - event control with intra-assignment delay

## Procedural Block

```
Type_of_block @ (sensitivity_list)
  begin : name_of_block
    local variable declarations;
    procedural assignment statements;
  end
```

## Blocking Assignments

- Blocking Assignment are represented with the sign "="
- These are executed sequentially, i.e. one statement is executed then the next statement is executed.
- One statement blocks the execution of other statements until it is executed.
- Any delay attached is also got added to delay in execution of next statements.

## Non-blocking Assignments

- A non-blocking assignment is represented with the sign "<="
- Its execution is concurrent with that of the following assignment or activity
- For all the non-blocking assignments in a block, the right-hand sides are evaluated first. Subsequently the specified assignments are scheduled
- It is illegal to use a non-blocking assignment in a continuous assignment statement or in a net declaration
- The order of the execution of distinct non blocking assignments to a given variable shall be preserved.
- Usually increases hardware

> Example Images and Code

## Coding Guidelines

- It is best to use blocking assignments when describing combinational circuits, so as to avoid accidentally creating a sequential circuit.

- Use Non-blocking assignments when describing sequential circuits.

- Do not mix blocking and non blocking assignments in the same always block
- When combining combinational and sequential code into a single always block, code the always block as a sequential always block with non blocking assignments.

## if else Statement
```
if (condition)
  begin // Alternative 1
    assignment1;
  end
else if (condition 2)
  begin // Alternative 2
    assignment2;
  end
else
  begin // Alternative 3
    assignment3;
  end
```

## Case Statements

- Multiway decision statement that tests whether an expression matches one of a number of other expressions and branches accordingly

```
case (expression)
  case_item_1 : statement 1;
  case_item_2, case_item_3  : statement_2;
  case_item_4 : statement 3;
  .....
  default : default_statement;
endcase
```

## Loop Statements

### for loop

- Its execution is a three-step process, as follows:

a. Initialize a variable that controls the number of loops executed.

b. Evaluates an expression if the result is zero, the loop exits, and if it is not zero, the for-loop executes its associated statement(s) and then perform step c.

c. Executes an assignment, normally modifies the value of the loop-control variable, then repeats step b.

```
for (i=0; i<10; i=i+1)
  begin
  ...
  end
```

### while loop
- Executes a statement until the expression becomes false.

- If the expression starts out false, the statement does not execute at all.
- Not synthesizable

```
while(condition)
  begin
  ...
  end
```

### repeat, forever loops

- Repeat executes a statement, fixed number of times.

- If the expression evaluates to unknown or high impedance, it is treated as zero, and no statement is executed.

- Forever continuously executes a statement
- Not synthesizable

## Functions

- Functions can enable other functions but not another task
- Functions always execute in zero simulation time
- Functions must not include delay, timing or timing control statements
- Functions must have at least one input argument
- Functions return a single value. They cannot have output or inout arguments

```
function [width] function_name (input input_args);
  begin
    //function_body;
  end
endfunction


// Example parity_cal
reg [31:0] address;

function parity cal;          //function declaration
  input [31:0] data;
  begin
    parity_cal = ~ ^ data;
  end
endfunction

always@ (address)
  parity reg = parity_cal(address);   //function call
```

## Tasks

- Tasks can enable other tasks and functions
- Tasks may execute in non-zero simulation time
- Tasks may include delay, timing or timing control statements
- Tasks may have zero or more arguments of type input, output or inout
- Tasks do not return a value but can pass multiple values through output and inout arguments

```
task task_name (input/inout/output args);
  begin
    //task_body;
  end
endtask


// Example parity_cal
reg [31:0] address;
reg parity_reg;

task parity cal;          //task declaration
  input [31:0] data;
  output parity;
  begin
    #1 parity_cal = ~ ^ data;
  end
endtask

always@ (address)
  parity reg = parity_cal(address, parity_reg);   //task call
```

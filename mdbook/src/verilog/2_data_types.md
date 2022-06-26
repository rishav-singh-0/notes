# Verilog Data Types

## Data Types

### Values and Strength
- Values
  - 0 : represents a logic zero, or a false condition
  - 1 : represents a logic one, or a true condition
  - x : represents an unknown logic value
  - z : represents a high-impedance state

- Strength

  - Strongest signal prevails
  - Useful for switch level modelling and not for RTL
  - When two signals with opposite value and same
strength combine, the resulting value is x

By default every variable will have 'x' value.
In case of tristate buffer it will have high impedance 'z'.

Strength levels are used in switch level modeling using cmos for building the circuit and not used for rtl.

## Numbers

```
<size>'<base><number>
```

- size = number of bits
- base = binary(b), octal(o), decimal(d), hexadecimal(h)
- number = 0-9, a-f, x, z

- For example: `4'b0010`
- `12'o43xz` will be expanded like: 
  ```
  4    3    x    z 
 100  011  xxx  zzz
  ```

- Underscores improve readability
eg. `32’h a_bc_2` is the same as `32’b 1010_1011_1100_0010`

- Zero, X and Z extension
  - `4'b1` is the same as `4'b 0001`
  - `4'bx1` is the sameas `4'b xxx1`
  - `4'bz1` s the same as `4'b zzzl`

- Unsized numbers will have by default 32 bit
  - `'h4a` is the same as `32'b 0000_0000_0100_1010`

## NET and REG
Data types in Verilog are divided into NETS and Registers.

### Nets - (net Data Type)

The nets variables represent the physical connection between structural
entities. These variables do not store values (except trireg); have the value
of their drivers which changes continuously by the driving circuit. Some net
data types are wire, tri, wor, trior, wand, triand, tri0, tri1, supply0,
supply1 and trireg. wire is the most frequently used type.
A net data type must be used when a signal is:
- driven by the output of some device
- declared as an input or in-out port
- on the left-hand side of a continuous assignment

Declaration and Assignment:
```
wire A, B, C
assign C = A & B
```

By default all the ports are wire datatype

- Nets are continuously driven by combinational logic

### Regs - (reg Data Type)

The register variables are used in procedural blocks which store values from
one assignment to the next. An assignment statement in a procedure acts as a
trigger that changes the value of the data storage element. Some register data
types are: reg, integer, time and real.

**Reg** is used for describing logic, **integer** for loop variables and
calculations, **real** in system modules, and **time** and **realtime** for
storing simulation times in test benches.

- Using **reg** does not means we will get physical hardware Registers. It depends on coding style not on the datatype.
- Assignments — Registers and nets can be mixed

### Port Assignments
- Input, Output and Inout - by default are wire datatype

![image]()

## Integers Data Type

- Integers store values as signed quantities
- Mostly synthesizable
- Arithmetic operations performed on integer variables produces 2's compliment result
- Procedural assignments shall be used to trigger value changes in integers

## Real Data Type

- Allows decimal and scientific notation
- Example: `0.210, 3.1415, 4.6e-2, -2.5`
- Not synthesizable
- Declaration and Assignment:

  ```
  real real_num;
  integer int_num;

  real_num = 67.9
  int_num = real_num;   <-- will roundoff to 68
  ```

## Time Data Type

- For storing and manipulating simulation time quantities
- Not synthesizable, useful for testbench implementation
- Declaration and Assignment:
  ```
  time sim_time;
  sim_time = $time;   <-- current simulation time will be assigned to variable sim_time
  ```

- The time variables behave same as a reg of at least 64 bits, with the least significant bit being bit 0
- The time variables are unsigned quantities, and unsigned arithmetic is performed on them


## Vectors

- Represent Buses
- Slices - range direction must be same as vector

For example: 
- `reg [3:0] z_bus;` where `z_bus[3]`=MSB and `z_bus[0]`=LSB

Scalar Array is an array of one 1-bit data type. Ex – reg a[3:0] - This is an
array of size 4 and where each element can hold 1-bit data. Vector Array is an
array of vectors. As we have seen earlier vectors are nothing but a group of
1-bit data types combined to increase the size of data type. Ex – reg [3:0] a
[7:0] - This is an array of size 8, where each element can hold 4-bit reg data.


## Arrays

- Arrays for variables types (reg, integer, time,real,realtime) are possible.

- Net Arrays:

```
  reg my_reg [0:5];        // Declares an array of 6, 1 bit registers
  my_reg[2] = 1'b1;        //Assigns value 1 to the 3rd element of array

  reg arrayb [7:0] [0:255]; // Declares a two dimensional array of
                            // one bit registers
  arrayb[1][0] = 0;         // Assigns 0 to the bit referenced by indices [1] [0]

  wire w_array [7:0] [5:0]; // Declares a two dimensional array of wires

  integer inta[1:64];       // Declares an array of 64 integer values
```

```
  reg [1:n] rega;    //n bit register (vector)

  reg rega [1:n];    //array of n, 1 bit registers
```

- Horizontal = vector, Vertical = array


## Memory

- A one dimensional array with elements of type reg
- Used to model ROMs, RAM, and reg files
```
  reg [7:0] mema [0:255]; // declares a memory mema of 256 8-bit
                          // registers. The indices are 0 to 255
  mema[1] = 0
```
- An n-bit reg can be assigned a value in a single assignment, but a complete memory cannot.
- Use for loop to initialize the whole memory

## Parameters

- Parameters are not variables, they are constants
```
module ram (clk,rst,din,radd,wadd,dout);

  parameter dt_width = 8; // Defines dt width as a constant value 8
  parameter ad_depth = 256; // Defines ad depth as a constant value 256

  ...
  reg [(dt_width - 1) : 0] mem [(ad_depth - 1) : 0];
    // Declaring a 256X8 memory using parameters
  ...

endmodule
```

- The parameter override values have to be contiguous, that is any parameter cannot be skipped during override
- Overriding a module's parameter values during initialization

```
module ram (clk,rst,din, radd wadd,dout) ;
  parameter dt_width = 8;
  parameter ad_depth = 256;
  ...
  reg [(dt_width - 1):0] mem [(ad_depth-1):0];
  ...
endmodule

//Assignment by ordered list

module system(...);
  input  rst,clk;
  output dout, done;

  //Overriding dt_width only
    ram #( 16 ) MEM1 (.clk(clk),.rst(rst),...);

  //Overriding both dt_width and ad_depth
    ram #( 16, 512) MEM2 (.clk(clk),.rst(rst),...):

endmodule

// Assignment by name

module system(...);
  input rstrclks 5
  output dout, done;

  //Overriding dt_width only
  ram #( .dt_width(16) ) MEM1 (.clk(clk),.rst(rst),...):
  
  //Overriding ad_depth only
  ram #( .ad_depth(512) ) MEM2 (.clk(clk),.rst(rst),...):

  //Overriding both dt_width and ad_depth
  ram #(.dt_width(16), .ad_depth(1024) ) MEM3 (.clk(clk),...):

endmodule
```


## String 

- A string is a sequence of characters enclosed by double quotes ("") and contained on a single line
- 8-bit ASCII value represents one character

```
reg [8*12:1] string_reg;
  // 13 characters requires a 8*12, or 96 bits wide reg
string_reg="Some text...";
```


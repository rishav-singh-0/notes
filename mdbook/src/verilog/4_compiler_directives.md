# Compiler Directives and System Tasks

## Internal variable monitoring system tasks
- $display, $write, $strobe, $monitor

- $display or $write displays the specified variables once when the command is executed in the code flow
- $display automatically adds a newline character to the end of its output, whereas the $write task does not
```
// syntax
$display("mreg = %h hex, %d decimal", mreg, mreg);
```
- $strobe display simulation data at a selected time (at the end of the current simulation time), when all the simulation events that have occurred for that simulation time
- Each time a variable or an expression in the argument list changes value, the entire argument list is displayed at the end of the time step.


## Simulation Time related Tasks
- $time - Returns an unsigned integer that is a 64-bit time, scaled to the timescale unit of the module that invoked it

## File input and output system tasks
- $fopen, $fclose, $readmemb

- The function $fopen opens the file specified as the filename argument and returns either a 32 bit multichannel descriptor, or a 32 bit file descriptor.
- The channel descriptor for each channel is a 32 bit value with only one bit set that corresponds to the channel number
- $fmonitor used to write within the file
- $stop causes simulation to be suspended
- $finish makes the simulator exit and pass control back to the host operating system
- $finish(2) will print the CPU usage time

## Probabilistic distribution function system text

$random
- The function returns a new 32-bit random signed integer number each time it is called
- Seed parameter controls the numbers that $random returns
```
reg [23:0] rand, seed num;
rand = Srandom (seed num);
```

## Compiler directives

- \`include, \`define , \`timescale

### \`define

- Creates a macro for text substitution
- Can be used both inside and outside module definitions
- Can be used in the source description by using the ( \` ) character, followed by the macro name
```
`define dt_width 8
`define ad_depth 256
```

### \`include

- Used to insert the entire contents of a source file in another file during compilation
- Used to include global or commonly used definitions and tasks

```
//File - state_definition.v

`define HOLD 0
`define RESET 1
`define SET 2
`define TOGGLE 3

//Main file

`include "state_definition.v"

```

### \`timescale

- Specifies the time unit and time precision of the modules that follow \`timescale
- time_unit specifies the unit of measurement for times and delay
- time_precision specifies how delay values are rounded before being used in simulation
- time_unit > time_precision
- Error if some modules have a \`timescale specified and others do not

```
`timescale time_unit / time_precision
`timescale 10ns / 10ps
```



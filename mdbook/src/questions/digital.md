# Digital Electronics

### What is TTL! State the voltage ranges of different TTL states
- TTL stands for Transistor Transistor Logic. According to the TTL standards,
  voltage of LOGIC HIGH state ranges from 2V to 5V and the voltage range of
  LOGIC LOW state is between 0V and 0.8V,

### What does CMOS stand for? Give the voltage ranges of the different states defined by the CMOS logic
- CMOS stands for Complementary Metal Oxide Semiconductor. In CMOS logic,
  voltage of HIGH state ranges from 3.5V to 5V while the voltage range of LOW
  state is 0V to 1.5V.

###  Draw the symbol of 4 bit ripple carry adder. 

### What is decoder
- When n-bit binary information is fed into a Decoder, it converts it to 2^n
  unique outputs.

### Define Flip-Flop
- A flip flop is a single bit storage element which can store one bit of
  information when given power supply.As long as power is fed in, the storage
  will n. Else, the data is lost.

### How is flip flop different from latch?
- Flip flops are different from latch.The output of the latch is affected
  consistently by the inputs when the enable is asserted. But, when we take
  flip flop into consideration, the output will be changed during rising or
  falling edge of the clock pulse.

### What are the types of flip flops you are aware of?
- D-Flip flop, JK Flip flop,T Flip flop, SR Flip flop

###  Define setup time and hold time
- Setup time is defined as the minimum amount of time the data signal should be
  held steady before the clock event so that the data are reliably sampled by
  the clock.
- Hold time is the minimum amount of time the data signal should be held steady
  after the clock event so that the data are reliably sampled.

### Hazards related to setup and hold time and how to solve them

### How did ring counter get its name?
- It may be visualized as a circulating shift register. The output of the MSB
  (last flip flop in the circuit) will be fed back to the input of the first
  flip flop, i.e. LSB.A 4 bit ring counter would be sufficient to understand
  the concept. The circuit is designed in such a way that only one | is kept
  circulated and it is done in synchronization with the clock pulses.

### How is a ring counter different from Johnson counter?
- In a Johnson counter, the output from the last flip flop is inverted and fed
  into the first one, and then shifting is carried out, whereas this inversion
  is not carried out in case of normal ring counter.

### Sync and Async Reset

### Problems related to async resets
- In async reset the glitch in reset signal directly effects the output(cause
  it does not care about clock)
- Bad timing of async reset could happen

### Clock Freq of FPGA, why can't go beyond specified freq

### If There Is An Asynchronous Feedback Loop What Is The Problem?
- If there is an asynchronous loop in the design the circuit becomes
  oscillatory or it may reach a stable state where it might get hung and it
  could not get out.

### If An Oscillatory Circuit Is There; What Happens During (a) RTL Synthesis (b) Simulation?
- During the RTL synthesis, the synthesis tool will give a warning during
  synthesis about the combinatorial feedback loop.
- During the simulation the simulation will get stopped saying the Iteration
  limit reached.

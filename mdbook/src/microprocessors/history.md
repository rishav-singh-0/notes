# Introduction to the Microprocessor and Computer

The world’s first microprocessor, the Intel 4004, was a 4-bit
microprocessor–programmable controller on a chip. It addressed a mere 4096,
4-bit-wide memory locations. The 4004 instruction set contained only 45
instructions. It was fabricated with the then-current state-of-the-art
P-channel MOSFET technology that only allowed it to execute instructions at the
slow rate of 50 KIPs (kilo-instructions per second).
This was slow when compared to the 100,000 instructions executed per second by
the 30-ton ENIAC computer in 1946. The main difference was that the 4004
weighed much less than an ounce. The main problems with this early microprocessor
were its speed, word width, and memory size.

## The 8085 Microprocessor

In 1977, Intel Corporation introduced an updated version of the 8080—the 8085.
The 8085 was to be the last 8-bit, general-purpose microprocessor developed by
Intel. Although only slightly more advanced than an 8080 microprocessor, the
8085 executed software at an even higher speed. An addition that took 2.0 μs
(500,000 instructions per second on the 8080) required only 1.3 μs (769,230
instructions per second) on the 8085. The main advantages of the 8085 were its
internal clock generator, internal system controller, and higher clock
frequency. This higher level of component integration reduced the 8085’s cost
and increased its usefulness. 

The 16-bit microprocessor evolved mainly because of the need for larger memory systems.
The popularity of the Intel family was ensured in 1981, when IBM Corporation decided to use
the 8088 microprocessor in its personal computer. The 16-bit 8086 and 8088 provided 1M byte of memory.

## The 80286 Microprocessor

The 80286 microprocessor (also a 16-bit architecture microprocessor)
was almost identical to the 8086 and 8088, except it addressed a 16M-byte memory system instead
of a 1M-byte system. The instruction set of the 80286 was almost identical to the 8086 and 8088,
except for a few additional instructions that managed the extra 15M bytes of memory. The clock
speed of the 80286 was increased, so it executed some instructions in as little as 250 ns (4.0 MIPs)
with the original release 8.0 MHz version. Some changes also occurred to the internal execution of
the instructions, which led to an eightfold increase in speed for many instructions when compared to
8086/8088 instructions.

## The 32-Bit Microprocessor

Applications began to demand faster microprocessor speeds, more
memory, and wider data paths. This led to the arrival of the 80386 in 1986 by Intel Corporation.
The 80386 represented a major overhaul of the 16-bit 8086–80286 architecture. The 80386 was
Intel’s first practical 32-bit microprocessor that contained a 32-bit data bus and a 32-bit memory
address.

The 80386 was available in a few modified versions such as the 80386SX, which
addressed 16M bytes of memory through a 16-bit data and 24-bit address bus, and
the 80386SL/80386SLC, which addressed 32M bytes of memory through a 16-bit data
and 25-bit address bus. An 80386SLC version contained an internal cache memory
that allowed it to process data at even higher rates. In 1995, Intel released
the 80386EX microprocessor. The 80386EX microprocessor is called an embedded PC
because it contains all the components of the AT class personal computer on a
single integrated circuit. The 80386EX also contains 24 lines for input/output
data, a 26-bit address bus, a 16-bit data bus, a DRAM refresh controller, and
programmable chip selection logic.

## The 80486 Microprocessor.

In 1989, Intel released the 80486 microprocessor, which incorpo- rated an
80386-like microprocessor, an 80387-like numeric coprocessor, and an 8K-byte
cache memory system into one integrated package. Although the 80486
microprocessor was not radi- cally different from the 80386, it did include one
substantial change. The internal structure of the 80486 was modified from the
80386 so that about half of its instructions executed in one clock instead of
two clocks. Because the 80486 was available in a 50 MHz version, about half of
the instructions executed in 25 ns (50 MIPs). The average speed improvement for
a typical mix of instructions was about 50% over the 80386 that operated at the
same clock speed. Later versions of the 80486 executed instructions at even
higher speeds with a 66 MHz double-clocked version (80486DX2). The
double-clocked 66 MHz version executed instructions at the rate of 66 MHz, with
memory transfers executing at the rate of 33 MHz. (This is why it was called a
double-clocked microprocessor.) A triple-clocked version from Intel, the
80486DX4, improved the internal execution speed to 100 MHz with memory
transfers at 33 MHz. Note that the 80486DX4 microprocessor executed
instructions at about the same speed as the 60 MHz Pentium. It also contained
an expanded 16K-byte cache in place of the standard 8K-byte cache found on
earlier 80486 microprocessors. Advanced Micro Devices (AMD) has produced a
triple-clocked version that runs with a bus speed of 40 MHz and a clock speed
of 120 MHz. The future promises to bring microprocessors that internally
execute instructions at rates of up to 10 GHz or higher.

## Pentium II and Pentium Xeon Microprocessors

The Pentium II microprocessor (released in 1997) represents a new direction for
Intel. Instead of being an integrated circuit as with prior ver- sions of the
microprocessor, Intel has placed the Pentium II on a small circuit board. The
main reason for the change is that the L2 cache found on the main circuit board
of the Pentium was not fast enough to function properly with the Pentium II. On
the Pentium system, the L2 cache oper- ates at the system bus speed of 60 MHz
or 66 MHz. The L2 cache and microprocessor are on a circuit board called the
Pentium II module. This onboard L2 cache operates at a speed of 133 MHz and
stores 512K bytes of information. The microprocessor on the Pentium II module
is actually Pentium Pro with MMX extensions.

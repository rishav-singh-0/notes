# General purpose registers in 8086 microprocessor

General purpose registers are used to store temporary data within the microprocessor. There are 8 general purpose registers in 8086 microprocessor.

![memory-segment](./images/memory-segment.png) 


AX, BX, CX, DX are of 16 bits and is divided into two 8-bit registers XH and XL to also perform 8-bit instructions.
SP, BP, SI, DI are of 16 bits and cannot be devided.

1. AX 
- This is the accumulator. 
- It is generally used for arithmetical and logical instructions but in 8086 microprocessor it is not mandatory to have accumulator as the destination operand.
Example:
```
ADD AX, AX  //(AX = AX + AX)
```

2. BX 
- This is the base register. 
- It is used to store the value of the offset.
Example:
```
MOV BL, [500] (BL = 500H)
```

3. CX 
- This is the counter register. 
- It is used in looping and rotation.
Example:
```
MOV CX, 0005
LOOP
```

4. DX 
- This is the data register. 
- It is used in multiplication an input/output port addressing.
Example:
```
MUL BX (DX, AX = AX * BX)
```

5. SP (stack pointer)
- It points to the topmost item of the stack.
- If the stack is empty the stack pointer will be (FFFE)H.
- Stack is in Stack Segment, used during instructions like PUSH, POP, CALL, RET etc.
- It’s offset address relative to stack segment.

6. BP (base pointer)
- It is primary used in accessing parameters passed by the stack.
- It’s offset address relative to stack segment.

7. SI (source index register)
- It is used in the pointer addressing of data and as a source in some string related operations.
- It’s offset is relative to data segment.

8. DI (destination index register)
- It is used in the pointer addressing of data and as a destination in some string related operations.
- It’s offset is relative to extra segment.

####

### 1. Sign Flag (S) 
- After any operation if the MSB (B(7)) of the result is 1, it indicates the number is negative and the sign flag becomes set, i.e. 1. If the MSB is 0, it indicates the number is positive and the sign flag becomes reset i.e. 0.
- from 00H to 7F, sign flag is 0
- from 80H to FF, sign flag is 1
- 1- MSB is 1 (negative)
- 0- MSB is 0 (positive)

Example:

MVI A 30 (load 30H in register A)
MVI B 40 (load 40H in register B)
SUB B (A = A – B)
These set of instructions will set the sign flag to 1 as 30 – 40 is a negative number.

MVI A 40 (load 40H in register A)
MVI B 30 (load 30H in register B)
SUB B (A = A – B)
These set of instructions will reset the sign flag to 0 as 40 – 30 is a positive number.

Zero Flag (Z) – After any arithmetical or logical operation if the result is 0 (00)H, the zero flag becomes set i.e. 1, otherwise it becomes reset i.e. 0.
00H zero flag is 1.
from 01H to FFH zero flag is 0
1- zero result
0- non-zero result

Example:

MVI A 10 (load 10H in register A)
SUB A (A = A – A)
These set of instructions will set the zero flag to 1 as 10H – 10H is 00H

Auxiliary Carry Flag (AC) – This flag is used in BCD number system(0-9). If after any arithmetic or logical operation D(3) generates any carry and passes on to B(4) this flag becomes set i.e. 1, otherwise it becomes reset i.e. 0. This is the only flag register which is not accessible by the programmer
1-carry out from bit 3 on addition or borrow into bit 3 on subtraction
0-otherwise

Example:

MOV A 2B (load 2BH in register A)
MOV B 39 (load 39H in register B)
ADD B (A = A + B)
These set of instructions will set the auxiliary carry flag to 1, as on adding 2B and 39, addition of lower order nibbles B and 9 will generate a carry.

Parity Flag (P) – If after any arithmetic or logical operation the result has even parity, an even number of 1 bits, the parity register becomes set i.e. 1, otherwise it becomes reset i.e. 0.
1-accumulator has even number of 1 bits
0-accumulator has odd parity

Example:

MVI A 05 (load 05H in register A)
This instruction will set the parity flag to 1 as the BCD code of 05H is 00000101, which contains even number of ones i.e. 2.

Carry Flag (CY) – Carry is generated when performing n bit operations and the result is more than n bits, then this flag becomes set i.e. 1, otherwise it becomes reset i.e. 0.
During subtraction (A-B), if A\>B it becomes reset and if (A\<B) it becomes set.
Carry flag is also called borrow flag.
1-carry out from MSB bit on addition or borrow into MSB bit on subtraction
0-no carry out or borrow into MSB bit

Example:

MVI A 30 (load 30H in register A)
MVI B 40 (load 40H in register B)
SUB B (A = A – B)
These set of instructions will set the carry flag to 1 as 30 – 40 generates a carry/borrow.

MVI A 40 (load 40H in register A)
MVI B 30 (load 30H in register B)
SUB B (A = A – B)
These set of instructions will reset the sign flag to 0 as 40 – 30 does not generate any carry/borrow.

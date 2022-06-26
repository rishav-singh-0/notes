# Operators

## Logical Operators

- AND &&, OR ||, NOT !
- Evaluates to a single bit value (1-True, 0-False, X-Unknown)
- Any non-zero value means True
- Operation with Unknown(X) will result in Unknown(X)

## Bitwise Operators

- AND (&)
- OR (|)
- XOR (^)
- NEGATION (~)
- XNOR (~^ or ^~)

## Relational Operators

- AND (&)
- OR (|)
- XOR (^)
- NAND (~&)
- XNOR (~^ or ^~)
- NOR (~|)

## Shift Operators

- Shift Right (>>)
- Shift Left (<<)
- >> and << are Logical Shift Operators
- >>> and <<< are Arithmetic Shift Operators

- Result in same length as operand

```
a=5'b10100;
b=a<<<2;    //b == 5'b10000
c=a>>>2;    //c==5'b11101 ,vacated bit is filled with MSB if the left operand is signed
d=a<<2;    //d==5'b10000
e=a>>2;    //e==5'b00101
```

## Concatenation Operators

- It is the joining together of bits resulting from two or more expressions within `{ }`
- The concatenation operators are used to form a bit pattern by joining two or more expressions
- Operands must be sized

  ```
  reg a;
  req [2:0]b, c;
  reg [7:0]x, y, z;

  a = 1'b1; b = 3'b100; c = 3'b110;

  x = {a, b, c};            // x =01100110
  y = {b, 2'b01, a};        // y =00100011
  z = {x[1:0], b[2:1], c};  // z =01010110

  x = {{2{a}}, b, {2{c}}};  // x =11100110110
  ```

## Relational Operators

- >, >=, <, <=
- Evaluates to a single bit value 0 (False) or 1 (True)
- Operation with Unknown(X) will result in Unknown(X)

### Equality

- Logical: ==, !=
- Case: ===, !==    (not synthesizeable)

```
a=4'b1x0z; b = 4'b1x0z;

a == b // Evaluates to x
a != b // Evaluates to x
a === b // Evaluates to 1
a !== b // Evaluates to 0
```

## Conditional Operators

- conditional_expression ? true_expression : false_expression;

## Arithmetic Operators

- Multiplication [*]
- Add [+]
- Subtract [-]
- Division [/]
- Modulus [%]

- Expensive on gates
- Represent physical hardwares eg. `add` will represent adders gates

### Points to be noted

  ```
  integer i;
  reg [15:0] a,z;

  a = -4'd12;
  z = a/3;        //evaluates to 21841
  i = -12/3;      // i evaluates to -4
  i = - 'd12/3;   // i evalautes to
                  // (2^32 - 12)/3 = 1431655761

  a = -12/3       // a evaluates to 65532
                  // 65532 = 2's complement of -4
  ```
- Negative register values are stored as 2’s complement, but are treated by arithmetic operators as unsigned operands
-  if no base specifier is used





## References

- https://www.theoctetinstitute.com/content/verilog/arrays/

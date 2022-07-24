# Multiplexers

- It is a combinational circuit which have many data inputs and single output
  depending on control or select inputs
- For N input lines, log n (base2) selection lines, or we can say that for 2^n
  input lines, n selection lines are required
- Logic like if, else if, else statements
- 2x1 Mux
```
Y = S0'*D0 + S0*D1 
```

|S0   |Y    |
|:---:|:---:|
|0    |D0   |
|1    |D1   |

- 4x1 Mux
```
Y = S1'*S0'*D0 + S1'*S0*D1 + S1*S0'*D2 + S1*S0*D3
```

|S1   |S0   |Y    |
|:---:|:---:|:---:|
|0    |0    |D0   |
|0    |1    |D1   |
|1    |0    |D2   |
|1    |1    |D3   |

# Demultiplexers

# Decoder

# Encoder

# Parity Generator/Checker

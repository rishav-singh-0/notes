# C++ Interview Questions

1. What is the value of 'x' ?
```
int x=10;
sizeof(x++);
cout<<x;
```

Ans: 10, because sizeof() computes at compile time, so x++ never executes

2. auto, static, register, mutable, extern initialize with 0 (global scope
   variables are also initialized with 0) 
3. Type Conversion:
```
bool -> char -> short int -> int -> unsigned int -> long -> unsigned long -> long long -> float -> double -> long double
1    -> 1    -> 2         -> 4   -> 4            -> 8    -> 8             -> 8         -> 4     -> 8      -> 12 bytes
```

4. Difference between `endl` and `"\n"`
- `endl` flushes the buffer so it is slower than `\n`

5. use of `getline`
- `getline(cin, variable_name)` to store whole line in "variable_name", input could be separated with spaces


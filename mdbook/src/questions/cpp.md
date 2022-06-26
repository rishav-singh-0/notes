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

6. `x++` and `++x`
- `y = x++` ==> `y=x; x=x+1;`
- `y = ++x` ==> `x=x+1; y=x;` (y gets updated value of x)

7. Use of variable arguments in function
- Usage of ... in function argument: This spread operator is the indication of declaring the function as accepting variable arguments.
- va_list: Stores the list of variable arguments recieved.
- va_arg: Retrieves the next value in the va_list with the type passed as the parameter.
- va_end: Clean up the argument list.



What are the differences between C and C++? 
1) C++ is a kind of superset of C, most of C programs except few exceptions (See this and this) work in C++ as well. 
2) C is a procedural programming language, but C++ supports both procedural and Object Oriented programming. 
3) Since C++ supports object oriented programming, it supports features like function overloading, templates, inheritance, virtual functions, friend functions. These features are absent in C. 
4) C++ supports exception handling at a language level, in C exception handling, is done in the traditional if-else style. 
5) C++ supports references, C doesn't. 
6) In C, scanf() and printf() are mainly used input/output. C++ mainly uses streams to perform input and output operations. cin is standard input stream and cout is standard output stream.

There are many more differences, above is a list of main differences. 



What are the differences between references and pointers? 
- Both references and pointers can be used to change the local variables of one
  function inside another function. Both of them can also be used to save
  copying of big objects when passed as arguments to functions or returned from
  functions, to get efficiency gain. 
Despite the above similarities, there are the following differences between
references and pointers.

References are less powerful than pointers 
1. Once a reference is created, it cannot be later made to reference another
   object; it cannot be reseated. This is often done with pointers. 
2. References cannot be NULL. Pointers are often made NULL to indicate that
   they are not pointing to any valid thing. 
3. A reference must be initialized when declared. There is no such restriction
   with pointers

Due to the above limitations, references in C++ cannot be used for implementing
data structures like Linked List, Tree, etc. In Java, references don’t have the
above restrictions and can be used to implement all data structures. References
being more powerful in Java is the main reason Java doesn’t need pointers.
References are safer and easier to use: 
1) Safer: Since references must be initialized, wild references like wild pointers are unlikely to exist. It is still possible to have references that don’t refer to a valid location (See questions 5 and 6 in the below exercise ) 
2) Easier to use: References don’t need dereferencing operator to access the value. They can be used like normal variables. ‘&’ operator is needed only at the time of declaration. Also, members of an object reference can be accessed with dot operator (‘.’), unlike pointers where arrow operator (->) is needed to access members.

What are virtual functions - Write an example? 
Virtual functions are used with inheritance, they are called according to the type of the object pointed or referred to, not according to the type of pointer or reference. In other words, virtual functions are resolved late, at runtime. The virtual keyword is used to make a function virtual.

Following things are necessary to write a C++ program with runtime polymorphism (use of virtual functions) 
1) A base class and a derived class. 
2) A function with the same name in a base class and derived class. 
3) A pointer or reference of base class type pointing or referring to an object of a derived class.

For example, in the following program bp is a pointer of type Base, but a call to bp->show() calls show() function of Derived class, because bp points to an object of Derived class.

C++


#include<iostream>
using namespace std;

class Base {
public:
    virtual void show() { cout<<" In Base \n"; }
};

class Derived: public Base {
public:
    void show() { cout<<"In Derived \n"; } 
};

int main(void) {   
    Base *bp = new Derived;     
    bp->show();  // RUN-TIME POLYMORPHISM
    return 0;
}

Output: 

In Derived

What is this pointer? 
The ‘this’ pointer is passed as a hidden argument to all nonstatic member function calls and is available as a local variable within the body of all nonstatic functions. ‘this’ pointer is a constant pointer that holds the memory address of the current object. ‘this’ pointer is not available in static member functions as static member functions can be called without any object (with class name).

Can we do "delete this"? 
See https://www.geeksforgeeks.org/delete-this-in-c/

What are VTABLE and VPTR? 
the vtable is a table of function pointers. It is maintained per class. 
vptr is a pointer to vtable. It is maintained per object (See this for an example). 
The compiler adds additional code at two places to maintain and use vtable and vptr. 
1) Code in every constructor. This code sets vptr of the object being created. This code sets vptr to point to vtable of the class. 
2) Code with polymorphic function call (e.g. bp->show() in above code). Wherever a polymorphic call is made, the compiler inserts code to first look for vptr using a base class pointer or reference (In the above example, since the pointed or referred object is of the derived type, vptr of a derived class is accessed). Once vptr is fetched, vtable of derived class can be accessed. Using vtable, the address of the derived class function show() is accessed and called.


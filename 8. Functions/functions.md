# Functions

These are blocks of code which can/cannot take some inputs and can/cannot return something

- CPP code always have **main function** which is called firstly.
- Main function is pushed to stack and then from it other functions are called, pushed to stack, executed and then control comes back to main.

```cpp

returnType name (args){
  ...
  return returnVal;
}
```

## Why Functions

1. **Reduce redundancy:** Put code into one function and use function everywhere.
2. **Make code modular:** Make it easy by putting different functionalities into different functions.
3. **Abstractions:** For example, Use library functions without knowing internals. It is abstraction given by functions.

## Inline Functions

Function calls have a overhead of calling the functions, pushing it into stack, control transfer etc.

To avoid all this in small function cases, we use inline functions

```cpp
inline int square (int x){
   return x*x;
}

int main (){
  square(2);
}
```

**Note:** inline function is just a request to the compiler regarding making it inline, it can decide not to make as well.

## Function Overloading

Same function name with different arguments.

## Default Args

We can give default args to functions

```cpp
int add (int a=1, int b=1, int c=1){
  return a + b + c;
}
```

**Note:** If you are not having default values to all args, then you can have values to last args only.
For example `int add (int x, int y=0, int z)` will generate error as middle arg can't have default arg, only z can have or both y and z or all x, y,z should be default args

## Problems

1. You need to declare or define the functions before the place it is being called. Otherwise it will be a **compiler error**.
2. If a function is declared but not defined, then it will be a **linker error**.
3. Function declaration can be `void func(int, int, char)` this much as well, in declaration arg names are not required.
4. What is the output

```cpp
int print (int x, int y, int z){
  cout<<x<<" "<<y<<" "<<z<<endl;
}

void main (){
  int i = 2;
  print(++i, ++i, ++i);
}

/**
 * Solution:
 * Compiler specific, depends on how and what order
 * is followed while executing the arguments.
 *
 * /
```

# Operators

## Arithmetic Operators

```cpp
Binary: +, -, *, /, %
Unary: ++, --
```

Postfix: x++ (Assigns then increments)
Prefix: ++x (Increments and then assigns)

**Note**: Don't use multiple unary operators like x++++x, x++/x++, x++\*++x etc. These are undefined behaviours as they are compiler specific then.

**Typecast**

int x = 50, y = 100;
`C style typecasting, this blindly typecasts`
double z = (double)x/y;

`Cpp style typecasting, static_cast casts after checking`
double z = static_cast\<double>x/y;

**CPP Precedence Table**
Order of precedence is defined by CPP standard.

1. Operators of high precedence are executed first.
2. Operators of different precedence are executed in order or associativity. Left to right or right to left.

[Reference for Order of precedence](https://en.cppreference.com/w/cpp/language/operator_precedence)

## Relational Operators

```cpp
==, !=, >=, <=, <, >
```

## Logical Operators

```cpp
&&, ||, !
```

**Note:** Remember that `&&` will not execute second expression if first is false, and `||` will not execute second if first one is true

## Assignment Operators

```cpp
=, +=, -=, *=, /=, %=, >>=, <<=
```

```cpp

//Associativity is Right to left for =
// So, y=20 then result is 20 and then x = 20
x = y = 20
=> (x = (y = 20))

// += has the second least precedence
// So 10+2 first and then x+=12
x += 10 + 2

// Result is x = 3
// Command is left to right associativity and gives second value
// x = ((1,2),3)
// x = (2,3) = 3
x = (1,2,3)

// x = 1,2,3 will be x = 1 as = has higher precedence
```

**Interesting Question**

```cpp
// What will be the output?
int a = 10, b = 20, c = 30;

if(c>b>a){
  cout<<"Yes";
}

/**
 * Solution:
 * Associativity left -> right
 * So c > b is true i.e 1
 * 1>a is false
 *
 * So, overall it is false.
 */
```

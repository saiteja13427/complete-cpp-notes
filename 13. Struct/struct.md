# Structs

Structs can be defined as user defiend data types which can hold many different datatype variables together.

### Declaration And Usage
1. 
```cpp
struct Point {
  int x;
  int y;
}

// We can initialise a struct and give its members values in multiple ways.
int main(){
  Point p;
  p.x = 1;
  p.y = 2;
}

// The following are c styled initialization of structs so might not work in some cpp compilers. But it worked when I tried
int main(){
  Point p = {1, 2};
}

// Here we skip x and only initialise y.
// In such cases x will get 0
int main(){
  Point p = {.y=2};
}

```

**Structure Pointers**
While using structure pointers, to access members we have to use ->

```cpp

struct Point {
  int x;
  int y;
}

int main(){
  Point p = {10, 20};
  Point *ptr = &p;
  // This is how you will access members using struct pointers
  cout<<p->x<<" "<<p->y<<endl;
}
```

We can also create structure arrays `Point arr[5];` and also pass them as arguments;

**Always pass structs by reference or by using pointers.**

### Struct vs Class
1. Struct members are public by default (we can make them private as well) whereas Class members are private by default.

Other than that everything is same, structs can also have functions, constructors etc.

Structures also supports inheritance  `struct child: parent {}`


### When to use structs vs when to use classes?
Structs can be used when we just want to bundle vars together.
Classes should be used when we care more about oops and are doing complex object oriented programming.


### Structure Alignment

Structure alignment is really important

```cpp
// Its size can be machine dependent.

// In Intel 64 bit architecture with GCC
// Size will be 24 bytes
// 1 byte + 7 byte padding
// 8 bytes
// 1 byte + 7 byte padding
struct S1 {
  char c1;
  double d1;
  char c2;
}

// 16 bytes
// 1 Byte
// 1 Byte + 6 bytes padding
// 8 bytes double
struct S1 {
  char c1;
  char c2;
  double d1;
}
```

Data types have alignment requirements
Like
1. Integer if it is 4 bytes then its starting address should end with 00
2. Doubles starting address should end with 000 and so on.

Thats why after char we get some padding and then put in double.

Also struct should be aligned with the largest member.
Thus 7 bytes after second char in first struct.

**Always declare the variables in struct in ascending or descending order of there sizes.**

Alignment is done so as to let CPUs read complete data types in 1 cycle. Say a double is 8 bytes and 64 bit arch machine reads 8 bytes in one, so if it is not aligned, cpu will have to read half of double in one cycle and next half in next cycle.

Compilers automatically handle alignemnts.

### Packed

```cpp
struct s {
  double d1;
  char c1;
  char c2;
} __attribute__((packed))
```
This will tell gcc and some compilers to do a compact respresentation.

Now the size will be 10 and not 16 as we have specified it to the compiler to make it compact.


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


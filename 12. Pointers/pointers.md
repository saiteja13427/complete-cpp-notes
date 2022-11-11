# Pointers

A variable which stores addresses of other variables

## Operators
***&*** = Before any variables except while declaration gives the address of the variable
**\*** = Dereferencing operator, used with address gives the value at that address.

```cpp
// Pointer vs reference
int *x; // Creates a pointer variable
int &x; // Creates a reference variable

int *x = &y; // x stores the address of y
int &x = y; // x is a reference to y
```

**NOTE:** Data type of the pointer tells the data type of the variable whose address is being stored in the pointer.

**Example:**

1. 
```cpp
int main(){
  int x = 10;
  int *y = &x;

  cout<<*y; //10
  x = x+10;
  cout<<*y; //20;
  *y = *y+10;
  cout<<x; //30
}
```

2. 
```cpp

int main(){
  int *ptr;
  cout<<ptr;
  cout<<*ptr; // Can give segmentation fault, as we are derefencing a random address. Random address as ptr is not initialised.
}
```

3. 
```cpp

int *x;
double *y;
string *z;

// All the pointer sizes will be same, the data type is just for compiler to know which data type are you dereferencing to when you infact dereference it.
// Depending of the compiler, the size of addresses may vary
sizeof(x) = sizeof(y) = sizeof(z)

```


## Applications
**NOTE:** In CPP, references are better as they are clean but in C as references are not there, pointers are the only choice.
1. Function parameters as pointers.
```cpp
int swap(int *x, int *y){
  int temp = *x;
  *x = *y;
  *y = temp;
}

int main(){
  swap(&a, &b);
}
```
2. Prevent large objects copy while passing to functions
```cpp
int func(vector<int> *v){

}

int main(){
  vector<int> nums;
  func(&nums);
}
```

3. Dynamic Memory Allocation
4. DS like Linkedlist, Tree, etc
5. System level programming.
6. To return multiple values from functions. Say we want to get two values from a function, then we can pass addresses of two variables, get result into it and use it from caller function.
7. Accessing array elements.
```cpp
int arr[] = {1,2,3};
// This is how compiler internally gets arr[2];
*(arr+2) //will give 3;

// Pointer arithmetic works like this
// arr + 1 will add 1*(size of data type of arr) say if it is int then it will 1*(4) assuming 4 bytes is the size of int in our compiler
```
8. We always pass address of arrays in c and cpp
```cpp
int func(int *arr (or) int arr[]){
 // As it is always address, never use sizeof to find array length in functions.
}

func(arr)
```
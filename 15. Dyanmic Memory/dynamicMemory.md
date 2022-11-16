# Dyanmic Memory Allocation

Dynamic memory allocation is where we can dynamically allocate memory at runtime.

Memory Layout
Stack ↓ (Growth direction)
Heap ↑ (Growth direction)
Data 
Code/Text

- Static variables and global variables are stores in data section

- Local varibles are stored in activation record of that function which is created in the stack.

- Pointer variables which we allocate dynamic memory with are also stored in activation record. But it points to a address which is in heap memory.

- All the dynamic memory is allocated in heap.

```cpp
int *p;
p = new int[5]; //--> Allocation of array of interger
delete [] ptr; // --> Deletes the whole array
ptr = null; // Good practise so that we don't access deallocated memory.
```

## Example

**Not working**

```cpp
/* This might give error, segmentation
fault because func is returning address of
a which is no more there as its call is
completed and will be removed from the call stack.*/
int *func(){
  int a = 10;
  int *ptr = &a;
  return ptr;
}

int main(){
  cout<<*func();
}
```

**Working**
```cpp
/* This works because ptr is now pointing to a memory location in heap which stays even after func call is completed.*/
int *func(){
  int *ptr = new int;
  *ptr = 10;
  return ptr;
}

int main(){
  cout<<*func();
}
```

### new Operator
1. It is an operator
2. Returns the address. `new int` return `int*` type pointer.
3. Better than malloc, calloc etc, used always in dynamic memory alloc.
4. Calls constructor for struct or class.
5. Can initialise value also. `int *p = new int(5)` 5 will be initialised in the allocated memory.
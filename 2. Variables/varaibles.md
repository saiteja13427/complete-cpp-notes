# Variables

**Naming Rules**

1. Variables can contain uppercase, lowercase, numbers, underscores.
2. Variables can't start with a number.

**Data Type**

1. **char**: 1 byte
2. **int**: 4 bytes
3. **long int**: 4 bytes
4. **long long int**: 8 bytes
5. **float**: 4 bytes
6. **double**: 8 bytes
7. **unsigned int**: Same as int but all positive range
8. **unsigned char**
9. **bool**: true or false (1 byte but can be optimised)

- Sizes of data types are compiler specific use `sizeof` to know data type size.
- Unitialised variable can have any grabage in cpp.

**Scope**

Cpp looks for a variables in its closes scope

```cpp
// No error in this prorgam
int x
int main () {
  int x = 10;
  cout<<x<<endl; // Prints 10
  {
    int x = 20;
    cout<<x<<endl; // Prints 20
  }
}
```

**Variable Types**

1. **Global Variables**: Variables declared globally. These are initialised and don't have gardbage in it.
2. **Static Variables**: These are variables which will be static, they are created once and will be there till program lifetime. These are also intialised as 0.
3. **const variables**: Cannot be modified.

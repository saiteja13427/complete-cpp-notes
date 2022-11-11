# References

1. Create an alias
2. Implemented using constant pointers
3. Assigned when they are declared as they are implemented using constant pointers.
4. Once a reference is created and referred, it cannot change.
5. `int &ref = NULL` is not allowed.
6. References are easy to use.

```cpp
int x = 10;
//y is a reference to x
int &y = x; 

// Note: Once a reference is attached, we can't change it
```

## Applications
1. To pass variables to functions by reference
2. Avoid copy of large objects during function calls. If we pass huge vectors normally to functions, then a copy of it is created which can be a wastage of memory. So pass such things by reference.
3. Modification in for each loop
```cpp
// This will not modify all the elements in vec
for(auto x: vec){
  x = x+5;
}

// To modify
for(auto &x: vec){
  x = x+5;
}
```
4. Avoide unnecessary copies of elements in for each loops
```cpp
// New x will be created and value will be copies and then printed
for(auto x: vec){
  cout<<x;
}

// Instead use &x
for(auto &x: vec){
  cout<<x;
}

// While using &x to not to accidentally modify x use const

for(const auto x: vec){
  cout<<x;
}
```


# Exception Handling

How do we do exception handling in cpp.

**Exceptions:**
A few examples of the exceptions in cpp are as follows: 
1. Divide by zero.
2. No heap memory available.
3. Accessing array elements outside of the allowed index range.
4. Pop from empty stack.

**Why Exception Handling in CPP?**
In complex software, we generally return special values like -1 in case of wrong inputs or exceptions with if statments.

But it is better to use exception handling so that the caller can be signalled and software can exit after a consistent state has been reached.

**Keywords:**
1. try
2. throw
3. catch

**Examples:**
1. 
```cpp
int main(){
  int x, y;
  cin>>x>>y;
  try {
    if(y==0) throw 0;
    cout<<"Output is"<<x/y;
  }
  catch(int x) {
    cout<<"Divisor is 0";
  }
}
```

2. 
```cpp
int main(){
  double x, y;
  cin>>x>>y;
  try {
    if(x==0.0) throw string("Hello World");
    if(y==0.0) throw 0;
    if(x+y==0.0) throw 0.1;
    cout<<"Output is"<<x/y;
  }
  // Need to have different catch blocks because there are different data type throws.
  catch(int x) cout<<"Divident is 0";
  catch(string x) cout<<x;
  // ... specifies any other data type throw here.
  catch(...) cout<<"Error";
}


```

**Note:** If there is a exception thrown and its data type is not handled by any catch and if a ... catch is also not there, then the **program will crash**

**Note:** If a functions throws an exception and doesn't catch it, then it is good to specify it in function declaration using throw keyword.

```cpp
int avg (int arr[], int n) throw (string, int) {

}
```

### Stack Unwinding
When a function throws exception then the control just goes up the stack through all the caller chain until its find the relevant catch block and skips anything until it finds the catch.

If a catch is not found then it crashes.
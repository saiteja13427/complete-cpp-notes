# IO

**Input Output in CPP**
cout, cin, cerr, clog

1. cout: Output to standard output
2. cin: Input from standard input
   Note: We can change cout and cin to take output intput from non standard devices as well.
3. cerr: Error on standard unbuffered error stream
4. clog: Error on standard buffered error stream

Standard output is generally console, monitor
Standard input is generally from keyboard

**Buffers**
cin and cout work with buffers, for examples

```cpp
cout<<"Enter x"<<endl;
cin<<x;
cout<<"Enter y"<<endl;
cin<<y;
cout<<x<<y<<endl;

// We can give
// 10 20 in one line itself
// And still x will be 10 and y will be 20
// As cin will take things from buffer
```

**New Line**
You can go with `\n` or `endl`

**Difference** is that \n will just add new line whereas endl will add new line and **flush the buffer**

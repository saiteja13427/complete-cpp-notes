# Loops

For any iterations, waiting, repeat something we need loops.

## Types of Loops

**1. For Loop**

```cpp
for(int i=0; i<10; i++)
  cout<<i;

cout<<i // Will give error due to scope
```

Used generally while iterating arrays, simple increment operations etc, we use for loops.

**2. While Loops**

```cpp
int i=0;
while(i<10){
  cout<<i;
  i++;
}
```

In more complex cases, wherein the increments vary depending on conditions etc, we use while loop.

3. do while loop

```cpp
int i=0;
do{
  cout<<i;
  i++;
}while((i<10))
```

To print atleast once.

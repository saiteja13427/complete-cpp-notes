# Unions
Unions are very much like structs syntactically but they are different in terms on memory allocation

### Declaration
```cpp
union Un {
  int x;
  double y;
}

int main (){
  Un u1;
  u1.x = 10;
  U *u2 = &u1;
  u2->x;
}
``

Unions allocate memory equivalent to the largest member and it can store any one of its members at once.

All the members point to same address location.

We can store an integer and get the character rep of it, store a float and get a integer rep of it and so on.
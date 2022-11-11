# Strings

## Declaration

### C Strings

```cpp
//C style string declaration
// Double quote will make it {'g', 'f', 'g', '\0'}
char st[] = "gfg";
// If you give size as 6 then the empty places will be filled with \0

char st[] = {'g', 'f', 'g', '\0'}
//Here if you don't put '\0' then if you do cout<<st, then you might get error, or garbage output after gfg as compiler will look for \0


```

**Functions in c styles**
1. **strlen**(str);
2. **strcmp**(s1, s2):
   s1 is smaller: negative
   s2 is smaller: positive
   s1==s2: 0
3. **strcpy**(s1, s2): copies s2 into s1; `As we can;t do char str[5]; str = "gfg", we use strcpy`
4. **strcat**: concatenation


### Cpp Strings (More recommended due to many reasons)

Why Cpp string?
1. Richer library
2. Supports many operators <, >, =, == etc.
3. Declare and assign later.
4. No worry about size.
5. Can be converted to c style.(`c_str()`)

```cpp
//Declaration
string str = "gfg";

//Length
str.length();

//Concat
str += "xyz";

//Substr .substr(start, length)
str.substr(1, 3)

// Find -> Gives index of first occurence
// If it is not present --> string::npause which tells no position found
str.find("eek");
```
Read word: `cin<<strVar`;
Read a line: `getline(cin, strVar, charWhereToStop)`;

Cpp strings can be accessed by index or using foreach also we can traverse.




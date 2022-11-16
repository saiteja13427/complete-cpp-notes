# Arrays

Arrays store data in contigous blocks of memory

```cpp
int arr[6] = {1,2,3,4,5,6};

int arr[] = {1,2,3,4,5};

int arr [2] {10, 20}

// Initialises the whole array with 0
int arr [6] = {0}

//arr -> Gives the address of first element
```

Without initialization, we get random garbage value only.

But

```cpp
int arr[6] = {10, 20}

// Then arr[2] - arr[5] will be zero
```

- CPP doesn't check for out of bounds, it may give error, may give random value.


**Length of array**
```cpp
sizeof(arr)/sizeoff(arr[0]);

// Not to be used when we recieve arr as a arg to funcion
```

**Advantage of array**
1. Randrom Access
2. Cache friendliness

**Limitation of array**
1. Some ops are slow.
2. Size has to be known


**Methods**

1. Max: `*max_element(arr, arr+n)`
2. Sum: `accumulate(arr, arr+n, 0)`


**2D Arrays**

Declaration

```cpp
int arr[3][2] = {{1,2},
                {3, 4},
                {5, 6}}
// Can be declared like this also
int arr[3][2] = {1,2,3,4,5,6}
```

They are stored in row major order i.e 2d array elements are also contigous as in first row is stored, then contigously next row and so on.

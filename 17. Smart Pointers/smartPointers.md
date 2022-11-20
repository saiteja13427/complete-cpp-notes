# Smart Pointers

**Problem with normal pointers:**
The problem with normal pointers is that if not deallocated, the memory stays allocated in cpp causing **memory leak.**

It can cause system crash as well if it keeps on running.

For example:

```cpp
//  This keeps on allocatine memory for integer and never deallocates it which will lead to memory leak and crash.
void run (){
  int *p = new int(6);
}

int main (){
  while(true){
    run();
  }
  return 0;
}

```

To automatically deallocate such memory, we bring in the concept of smart pointers.

### Template Smart Pointers
```cpp
Template<T>
class smart_pointer {
  T *ptr;
  public:
    smart_pointer(T *p){
      ptr = p;
    }
    ~smart_pointer(){
      delete ptr;
    }
    T & operator * (){
      return *ptr;
    }

    T & operator -> (){
      return ptr;
    }
};

int main (){
  smart_pointer<int> sp(new int());
  *sp = 6;
}

// Problem: 

int *p1 = new int(10);
{
  int *p2 = p1;
  smart_pointer<int> (p2);
}

// Once p2s scope ends, it will dellocate memory which contains 10. 
// But it was being referenced by p1 also which is still in scopr. In such case we can see errors.

// To overcome this problem we will have to have reference counters and deallocate only when reference count becomes 0. 

// This problem is solved by library implementations of smart pointers.
```

### Library Smart Pointers

#### unique_ptr: 

This is same as our implementation above wherein we can create a pointer of any type which will be deallocated once out of scope.

```cpp
unique_ptr<int> p(new int(5));
//Recommended way after c++14 as it is cleaner.
unique_ptr<int> p = make_unique<int>(5)
```

Note: One unique pointer cannot be assigned to another unique pointer. But it can be moved from one to another.
```cpp
unique_ptr<int> p1 = make_unique<int>(5);

// unique_ptr<int> p2 = p1; Not allowed
// The following is allowed and moved the ownership of the location
// completely to p2;

unique_ptr<int> p2 = move(p1);

// After moving if we try dereferencing p1, it may throw segmentation fault
```

#### shared_ptr: 

Shared pointers are the once wherein two or more pointers can point to the same location.

It is implemented by adding a overhead of maintaining reference count to all the memory locations.

```cpp
int main(){
  shared_ptr<int> p1 = make_shared<int>(5);
  // Points p2 to p1 and increments the reference count. 
  shared_ptr<int> p2 = p1;
  cout<<p1.use_count()<<endl; // 2: Gives the reference counts
  cout<<p2.use_count()<<endl; // 2
  return 0;
}

```

#### weak_ptr: 

Weak pointers are there to reference to a memory which is owned by a shared pointer.

Difference being that weak pointers will not increment the reference count of that shared pointer.

These are just used to create some temporary pointers wherein we don't want to increment reference count and all.


```cpp
int main(){
  weak_ptr<int> p1;
  {
    shared_ptr<int> p2 = make_shared<int>(5);
    p1 = p2;
  }
  // Here p2 will be deallocated so to check that for p1
  cout<<p1.expired(); // Return true if the memory it is pointing to is deallocated.
  return 0;
}

// To upgraded a weak pointer to a shared one
shared_ptr<int> p3 = lock(p1);

// Note: there is not make_weak function as in weak_ptr is always used to point to shared pointer addressess only and never used to own a memory location.

```

**Why Weak?**
In case there are two classes each having a shared pointer to the other class. There can be a cycling dependency due to which we won't be able to deallocate both the pointer memories.

In such cases we should use weak pointer in one class and shared in one.



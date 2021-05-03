# C++ Memory Model


### Key Concepts
- *Pointers* and *dereferencing*
- Local memory: **stack**
- Allocated memory : **heap**

---

> Every variable created are stored in stack.

variable's 4 elements
- name
- type
- value
- memory location ("memory address")

### & operator
return the memory address : *High memory address*

```C++
#include <iostream>

int main() {
    int num = 7;
    
    std::cout << "Value: " << num << std::endl;
    std::cout << "Address: " << &num << std::endl;

    return 0;
}
```

---

### Stack Memory 

- Stack memory's lifecycle is tied to the located func. 
    -> When the func. returns or ends the stack memory is released back to the system.
- Stack memory starts from high addressess and grows down


#### Pointer

- a variable that stores the memory address of the data
    -> a level of indirection from the data
- defined by adding an * to the type
    -> `int *p = &num;`


#### Dereference Operator

- retrieve value from an address

```C++
int main() {
    int num = 7;
    int *p = &num;
    int former_value = *p; // *p = 42;

    *p = 42; // change p's value from 7 to 42

    // -> 'num' contains a value 42, 'p' points the memory address of num
    // -> 'former_value' contains a value 7

    return 0;
}
```

#### Invalid memory : memory would be reused
- as stack is dislocated when func. is done, if I get memory address from one function and do another one, the address returned would be overwritten and 'a' would not what I expect.

```C++
int main() {
    int *p = functionReturnsAddress();
    otherFunction();
    double a = p->getSth();  // can't get the result I expected!

    return 0;
}
```

#### Wrap-up

```C++
#include <iostream>

int main() {
  int num = 7;
  std::cout << "num: " << num << std::endl;
  std::cout << "&num: " << &num << std::endl;

  int *p = &num;
  std::cout << "p: " << p << std::endl;
  std::cout << "&p: " << &p << std::endl;
  std::cout << "*p: " << *p << std::endl;

  *p = 42;
  std::cout << "*p changed to 42: " << std::endl;
  std::cout << "num: " << num << std::endl;

  return 0;
}
```

- Result would be like :

        num: 7

        &num: 0x7ffc30561ecc

        p: 0x7ffc30561ecc

        &p: 0x7ffc30561ed0

        *p: 7

        *p changed to 42: 

        num: 42


---

### Heap Memory

- memory independent of the lifecycle of a func.
- create with `new` operator

    -> `new` returns a **pointer** to the memory stroing the data

    -> **NOT** an instance of the data itself!

#### new operator
- allocate memory on the heap for the data structure
- initialize the data structure
- return a pointer to the start of the data structure 
> The memory is only retrieved when the pointer is passed to the delete operator
```C++
int *numPtr = new int;
// pointer numPtr in stack points new int in heap memory
```

#### null pointer
- when `delete` is done, the pointer points to memory that does not contain any data anymore
- `nullptr` points to the memory address `0x0` : "nowhere"
- `delete 0x0` is ignored
- accessing 0x0 generates `segmentation fault`
- should manually set pointer to `nullptr`
```C++
delete c;

c = nullptr;
```

#### Arrow Operator
- object stored via a pointer can be accessed using `->`
```C++
c->getVolume();
// identical to
(*c).getVolume();
```

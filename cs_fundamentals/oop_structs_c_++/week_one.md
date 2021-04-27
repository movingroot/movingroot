## C++

---
#### Types

##### Primivite Types
|Type|Description|
|:--:|:--|
|int|integer|
|char|single chars/byte|
|bool|Boolean|
|float|floating point num|
|double|double-precision f|
|void|absence of value|

- Use double much more than float

##### User-defined Types
|Type|Description|
|:--:|:--|
|std::string|sequence of chars|
|std::vector|dynamically growing array|

---
#### Sample code

```C++
int main() {
    int i = 4;
    i = i + 2;

    char c = 'a';

    std::cout << i << " " << c << std::endl;

    return 0;
}
```

---
#### Class

##### Encapsulation

- Enclose data&functionality into a single unit
* ###### Public
members can be accessed by client code
* ###### Private
only used within the class itself

- interface (.h) is defined separately from the implementation (.cpp)
* ###### Header File(.h)
define the interface to the class w/ member variables and functions

ex) Cube.h
```C++
#pragma once   // only compile this code once

class Cube {
    public:
        double getVolume();
        double getSurfaceArea();
        void setLength(double length);
    
    private:
        double length_;
};
```

* ###### Implementation File(.cpp)
contain the code to implement the class

ex) Cube.cpp
```C++
#include "Cube.h"

double Cube::getVolume() {
    return length_ * length_ * length_;
}

double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
}

void Cube::setLength(double length) {
    length_ = length;
}
```

ex) main.cpp
```C++
#include <iostream>
#include "Cube.cpp"

int main() {
    Cube c;

    c.setLength(3.48);
    double volume = c.getVolume();
    std::cout << "Volume: " << volume << std::endl;

    return 0;
}
```

---
#### C++ Standard Library ; std

* ##### iostream
operations for reading/writing

* Features can be imported into global space
    - ex) `using std::cout;`

ex) 
```C++
#include <iostream>

using std::cout;
using std::endl;

int main() {
    cout << "Hello, World!" << endl;

    return 0;
}
```

* can specify rather generic data structure within the user-defined namespace e.g. `uiuc::Cube`; encapsulating class into the namespace

```C++
#pragma once 

name uiuc {
    class Cube {
        ...
    };
}
```
* Should make it both for .h and .cpp


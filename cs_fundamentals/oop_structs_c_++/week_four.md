## Template

- take on different types when the type is initialized
- an array of objects in memory
- `std::vector` 
  - starndard library
  - **dynamically growing array** with a `templated` type

```C++
// define
#include <vector>

// initialize
std::vector<T> v;

// add to back of array
v.push_back(4); // add int 4 to vector v

// access
v[0];

// size
v.size();
```
ex)
```C++
#include <vector>
#include <iostream>

int main()
{
  std::vector<int> v;
  
  v.push_back(2);
  v.push_back(4);
  v.push_back(8);
  
  std::cout<< v[0] << std::endl;
  
  return 0;
}
```

---

### Templated Function
- declared before the beginning of a class or func.
- checked at compile time : errors can be caught before running
```C++
template <typename T>
class List
{
  ...
  private:
  T data_;
};

template <typename T>
int max(T a, T b)
{
  if (a > b) { return a; }
  return b;
}
```

---

## Inheritance
- allow a class to inherit all member func.s and data from a base class into a derived one

```C++
// Shape.h
class Shape
{
  public:
    Shape();
    Shape(double width);
    double getWidth() const;
  
  private:
    double width_;
};

// Cube.h
class Cube : public Shape 
{
  public:
    Cube(double width, double height);
    double getVolume() const;
  
  private:
    double height_;
};

// Cube.cpp
#include "Cube.h"
#include "Shape.h"

Cube::Cube(double width, double height) : Shape(width) 
{
  height_ = height;
}

double Cube::getVolume() const
{
  return getWidth() * getWidth() * getWidth();
}
```

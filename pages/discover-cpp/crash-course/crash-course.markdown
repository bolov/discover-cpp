---
title: Crash Course
tags: []
keywords: intro
summary: "Crash course into C++"
sidebar: discover_cpp_sidebar
permalink: crash-course.html
---

## About

This is a quick glimpse into C++.

It is intended or for those who are new to C++ and need a quick reference/reminder.


## Classes

### Defining classes, Data members & methods, Objects

You declare a class with the `struct` or `class` keyword:

```cpp
struct Empty_class {
};
```

A class has data members and methods:

```cpp
struct Point {
  float x; // data member
  float y;

  // method get_length:
  float get_length() const
  {
    return sqrt(x * x + y * y);
  }
};
```

+ A class only *describes* what an object is and how it behaves.

+ Data members are the object's properties.

+ Methods are actions that an object can do.

+ A class is a **user defined type**. Variables of class type are usually called *objects*,
or instances of the class

Creating objects (instantiating a class):

```cpp
Point p1; // p1 is a Point. x and y are uninitialized
Point p2{10.f, 20.f}; // p2 is a Point. x is 10.f and y is 20.f
```
Accessing data members and methods of objects is done via the
Structure reference (member) operator:

```cpp
Point p{10.f, 20.f};
p.x = 15.f;

cout << p.get_length() << endl; // prints 18.0277 (sqrt(15.f * 15.f + 20.f * 20.f))
```

### Constructors


Constructors (sometimes abbreviated `ctor`) are special methods that are called
when an object is created.

+ A ctor has the same name as the class
+ A ctor has no return type (not even `void`)

```cpp
struct Point {
  float x;
  float y;

  Point(float x, float y) // ctro with 2 parameters
    : x{x} // list initialization starts with :
      y{y} // each data member should be initialized
    {
      // body (empty in this example)
    }
};
```

+ data members can be in-class initialized:

```cpp
struct Foo {
  int a = 24;
  int b{12};
  int c{};
};
```

+ A ctor that accept no arguments is called a *default constructor*.

+ If no ctor is explicitly declared, a deafult one will be implicitly generated

+ Some special methods, default constructor included, can be defaulted. (`=default`)


```cpp
struct Point {
  float x = 0.f; // in-class data member initialization
  float y = 0.f;

  Point() = default; // request default constructor to be generated

  Point(float x, float y) // ctro with 2 parameters
    : x{x} // list initialization starts with :
      y{y} // each data member should be initialized
    {
      // body (empty in this example)
    }
};
```

+ Ctors can be delegated:


```cpp
struct Point {
  float x = 0.f; // in-class data member initialization
  float y = 0.f;

  Point()
    : Point(0.f, 0.f) // delegate to ctror with 2 params
  {
  }

  Point(float x, float y) // ctro with 2 parameters
    : x{x} // list initialization starts with :
      y{y} // each data member should be initialized
    {
      // body (empty in this example)
    }
};
```




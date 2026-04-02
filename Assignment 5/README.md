# Assignment 5 – Polymorphism: Virtual Draw Function

## Problem Statement

Develop a base Shape class with a virtual function for drawing. Create derived classes for Circle
and Rectangle that override the draw function. Write a program that uses polymorphism to call the
appropriate draw function for different shapes.

---

## Key Concepts

### Polymorphism
Polymorphism (meaning "many forms") allows a single interface to represent different underlying
types. In C++, runtime polymorphism is achieved using **virtual functions** and **pointers/references**
to a base class.

### Virtual Function
A virtual function is declared in the base class using the `virtual` keyword. When called through
a base-class pointer or reference, the overridden version in the derived class is executed.

### Pure Virtual Function / Abstract Class
If a virtual function is declared as `= 0`, it becomes a **pure virtual function** and the class
becomes **abstract** — it cannot be instantiated directly.

---

## Code

```cpp
#include<iostream>
using namespace std;

// Abstract Base Class
class Shape {
public:
    // Pure Virtual Function
    virtual void getArea() = 0; 
};

class Circle : public Shape {
public:
    void getArea() {
        int r;
        cout << "Enter circle radius: ";
        cin >> r;
        cout << "Area of circle is: " << (3.14 * r * r) << endl;
    }
};

class Rectangle : public Shape {
public:
    void getArea() {
        int l, b;
        cout << "Enter length and breadth: ";
        cin >> l >> b;
        cout << "Area of rectangle is: " << (l * b) << endl;
    }
};

class Triangle : public Shape {
public:
    void getArea() {
        int b, h;
        cout << "Enter base and height of triangle: ";
        cin >> b >> h;
        // Formula: 0.5 * base * height
        cout << "Area of triangle is: " << (0.5 * b * h) << endl;
    }
};

int main() {
    Circle c1;
    c1.getArea();

    Rectangle r1;
    r1.getArea();

    Triangle t1;
    t1.getArea();

    return 0;
}

```
```cpp
#include<iostream>
using namespace std;

// Abstract Base Class
class Shape {
public:
    // Pure Virtual Function
    virtual void getArea() = 0; 
};

class Circle : public Shape {
public:
    void getArea() {
        int r;
        cout << "Enter circle radius: ";
        cin >> r;
        cout << "Area of circle is: " << (3.14 * r * r) << endl;
    }
};

class Rectangle : public Shape {
public:
    void getArea() {
        int l, b;
        cout << "Enter length and breadth: ";
        cin >> l >> b;
        cout << "Area of rectangle is: " << (l * b) << endl;
    }
};

class Triangle : public Shape {
public:
    void getArea() {
        int b, h;
        cout << "Enter base and height of triangle: ";
        cin >> b >> h;
        // Formula: 0.5 * base * height
        cout << "Area of triangle is: " << (0.5 * b * h) << endl;
    }
};

int main() {
    Circle c1;
    c1.getArea();

    Rectangle r1;
    r1.getArea();

    Triangle t1;
    t1.getArea();

    return 0;
}
```

---

## Sample Output

```
--- Polymorphic draw() calls ---
Drawing Circle with radius = 5
Drawing Rectangle with length = 10 and breadth = 4
Drawing Triangle with base = 6 and height = 3
```

---

## How Polymorphism Works Here

1. `Shape*` pointers are used to store objects of derived classes (`Circle`, `Rectangle`, `Triangle`).
2. When `shapes[i]->draw()` is called, C++ uses the **vtable** (virtual function table) to dispatch
   the call to the correct overridden function at runtime.
3. Without `virtual`, the base class version of `draw()` would always be called — this is called
   **static (compile-time) binding**.
4. With `virtual`, the correct derived version is called — this is **dynamic (runtime) binding**.

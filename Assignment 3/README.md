# Assignment 3 – Constructors & Destructors: Circle and Rectangle

## Problem Statement

Define classes for Circle and Rectangle with constructors to initialize their dimensions and
member functions to calculate area and perimeter. Create objects and demonstrate their usage.

---

## Key Concepts

### Default Constructor
A default constructor takes no arguments. It initializes object data members with default values
when an object is created without passing parameters.

### Parameterized Constructor
A parameterized constructor accepts arguments to initialize object data members with user-defined
values at the time of object creation.

### Copy Constructor
A copy constructor creates a new object by copying the data of an existing object. It is invoked
when an object is initialized using another object of the same class.

### Destructor
A destructor is a special member function that is automatically called when an object goes out of
scope or is destroyed. It is used to release resources allocated to the object.

---

## Code

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    float radius, area, perimeter;

public:
    Circle() {
        radius = 0;
        cout << "Circle default constructor called" << endl;
    }

    Circle(float r) {
        radius = r;
        cout << "Circle parameterized constructor called" << endl;
    }

    Circle(Circle &c) {
        radius = c.radius;
        cout << "Circle copy constructor called" << endl;
    }

    void areaCalc() {
        area = 3.14 * radius * radius;
        cout << "Circle Area = " << area << endl;
    }

    void perimeterCalc() {
        perimeter = 2 * 3.14 * radius;
        cout << "Circle Perimeter = " << perimeter << endl;
    }

    ~Circle() {
        cout << "Circle destructor called" << endl;
    }
};

class Rectangle {
private:
    float length, breadth, area, perimeter;

public:
    Rectangle() {
        length = 0;
        breadth = 0;
        cout << "Rectangle default constructor called" << endl;
    }

    Rectangle(float l, float b) {
        length = l;
        breadth = b;
        cout << "Rectangle parameterized constructor called" << endl;
    }

    Rectangle(Rectangle &r) {
        length = r.length;
        breadth = r.breadth;
        cout << "Rectangle copy constructor called" << endl;
    }

    void areaCalc() {
        area = length * breadth;
        cout << "Rectangle Area = " << area << endl;
    }

    void perimeterCalc() {
        perimeter = 2 * (length + breadth);
        cout << "Rectangle Perimeter = " << perimeter << endl;
    }

    ~Rectangle() {
        cout << "Rectangle Destructor called" << endl;
    }
};

int main() {
    cout << "--- Circle Objects Demonstration ---" << endl;
    Circle c1;           // default constructor
    Circle c2(7);        // parameterized constructor
    Circle c3(c2);       // copy constructor

    c2.areaCalc();
    c2.perimeterCalc();

    cout << "\n--- Rectangle Objects Demonstration ---" << endl;
    Rectangle r1;           // default constructor
    Rectangle r2(10, 5);    // parameterized constructor
    Rectangle r3(r2);       // copy constructor

    r2.areaCalc();
    r2.perimeterCalc();

    return 0;
}
```

---

## Sample Output

```
--- Circle Objects Demonstration ---
Circle default constructor called
Circle parameterized constructor called
Circle copy constructor called
Circle Area = 153.86
Circle Perimeter = 43.96

--- Rectangle Objects Demonstration ---
Rectangle default constructor called
Rectangle parameterized constructor called
Rectangle copy constructor called
Rectangle Area = 50
Rectangle Perimeter = 30
Rectangle Destructor called
Rectangle Destructor called
Rectangle Destructor called
Circle destructor called
Circle destructor called
Circle destructor called
```

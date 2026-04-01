# Assignment 4 – Function Overloading: Arithmetic Operations

## Problem Statement

Create functions for arithmetic operations (+, -, *) that work with both integers and
user-defined classes (e.g., Point with X and Y coordinates) demonstrating function overloading.

---

## Key Concepts

### Function Overloading
Function overloading allows multiple functions to share the same name as long as their parameter
lists differ (in number, type, or order of parameters). The compiler selects the correct version
based on the arguments passed.

A function can be overloaded whether or not it is a member of a class.

---

## Code

```cpp
#include <iostream>
using namespace std;

class Point {
public:
    int x, y;

    Point(int a, int b) {
        x = a;
        y = b;
    }
};

// Overloaded functions for integers
int add(int a, int b) {
    return a + b;
}

void add(double a, double b) {
    double sum = a + b;
    cout << "Sum of both double data type operands = " << sum << endl;
}

int sub(int a, int b) {
    return a - b;
}

int mul(int a, int b) {
    return a * b;
}

// Overloaded functions for Point objects
Point add(Point p1, Point p2) {
    Point p(0, 0);
    p.x = p1.x + p2.x;
    p.y = p1.y + p2.y;
    return p;
}

Point sub(Point p1, Point p2) {
    Point p(0, 0);
    p.x = p1.x - p2.x;
    p.y = p1.y - p2.y;
    return p;
}

Point mul(Point p1, Point p2) {
    Point p(0, 0);
    p.x = p1.x * p2.x;
    p.y = p1.y * p2.y;
    return p;
}

void display(Point p) {
    cout << "(" << p.x << ", " << p.y << ")" << endl;
}

int main() {
    int a, b;
    cout << "Enter two integers: ";
    cin >> a >> b;
    cout << "Addition: " << add(a, b) << endl;
    cout << "Subtraction: " << sub(a, b) << endl;
    cout << "Multiplication: " << mul(a, b) << endl;

    double c, d;
    cout << "Enter two decimals: ";
    cin >> c >> d;
    cout << "Addition: ";
    add(c, d);

    Point p1(3, 4);
    Point p2(1, 2);

    cout << "\nPoint Operations:\n";

    Point p_add = add(p1, p2);
    Point p_sub = sub(p1, p2);
    Point p_mul = mul(p1, p2);

    cout << "Addition: ";
    display(p_add);

    cout << "Subtraction: ";
    display(p_sub);

    cout << "Multiplication: ";
    display(p_mul);

    return 0;
}
```
## Operator Overloading 

```cpp
 #include <iostream>
 using namespace std;

 class Number (
 public:
 int value;


Number(int v) {
value = v;
}

void operator++() {

value value + 3;


};

 int main() {
 Number n(5);


++n;


cout << n.value;


return 0;
}
```
---

## Sample Output

```
Enter two integers: 5 3
Addition: 8
Subtraction: 2
Multiplication: 15
Enter two decimals: 2.5 1.5
Addition: Sum of both double data type operands = 4

Point Operations:
Addition: (4, 6)
Subtraction: (2, 2)
Multiplication: (3, 8)
```

# Assignment 1 – Procedural vs Object-Oriented Approach

## Problem Statement

Write programs to solve a simple problem (e.g., calculating area) using both procedural and
object-oriented approaches. Compare the code structure, maintainability, and benefits of
object-oriented programming.

---

## Approach 1 – Switch-Case (Procedural)

```cpp
#include <iostream>
using namespace std;

int main() {
    int i;
    int n1, n2;
    cout << "\nint i =" << i << endl;
    float f;
    bool b;
    cout << "Float f =" << f << endl;
    cout << "Bool b = " << b << endl;
    cout << "\nEnter num1\n";
    cin >> n1;
    cout << "\nenter num2\n";
    cin >> n2;
    int sum = n1 + n2;
    cout << "\nSUM = " << sum << endl;

    while (1) {
        int ch;
        cout << "Menu - calculate area of :  1.circle   2.rectangle  3.triangle  4.square \n Volume of 5.cylinder 6. sphere 7.exit" << endl;
        cin >> ch;
        int area1, area2, area3, area4, area5, area6;
        switch (ch) {
        case 1: {
            int r;
            cout << "Enter Radius:";
            cin >> r;
            area1 = 3.14 * (r * r);
            cout << "area is = " << area1 << endl;
            break;
        }
        case 2: {
            int b, h;
            cout << "Enter breadth:";
            cin >> b;
            cout << "Enter height:";
            cin >> h;
            area2 = 0.5 * b * h;
            cout << "area is = " << area2 << endl;
            break;
        }
        case 3: {
            int l, w;
            cout << "Enter length:";
            cin >> l;
            cout << "Enter width:";
            cin >> w;
            area3 = l * w;
            cout << "area is = " << area3 << endl;
            break;
        }
        case 4: {
            int s;
            cout << "Enter side:";
            cin >> s;
            area4 = s * s;
            cout << "area is = " << area4 << endl;
            break;
        }
        case 5: {
            int h1, r1;
            cout << "Enter height:";
            cin >> h1;
            cout << "Enter radius:";
            cin >> r1;
            area5 = 3.14 * r1 * r1 * h1;
            cout << "area is = " << area5 << endl;
            break;
        }
        case 6: {
            int r2;
            cout << "Enter radius:";
            cin >> r2;
            area6 = (4.0 / 3.0) * 3.14 * r2 * r2 * r2;
            cout << "area is = " << area6 << endl;
            break;
        }
        case 7:
            cout << "exiting";
            return 0;
        default:
            cout << "invalid choice ";
            break;
        }
    }
}
```

---

## Approach 2 – Functions (Procedural)

```cpp
#include <iostream>
using namespace std;

float AreaC();
float AreaT();
float AreaR();
float AreaSq();
float VolCyl();
float VolS();

float AreaC() {
    float r;
    cout << "Enter Radius: ";
    cin >> r;
    float area = 3.14 * r * r;
    cout << "Area of Circle = " << area << endl;
    return area;
}

float AreaT() {
    float b, h;
    cout << "Enter breadth: ";
    cin >> b;
    cout << "Enter height: ";
    cin >> h;
    float area = 0.5 * b * h;
    cout << "Area of Triangle = " << area << endl;
    return area;
}

float AreaR() {
    float l, w;
    cout << "Enter length: ";
    cin >> l;
    cout << "Enter width: ";
    cin >> w;
    float area = l * w;
    cout << "Area of Rectangle = " << area << endl;
    return area;
}

float AreaSq() {
    float s;
    cout << "Enter side: ";
    cin >> s;
    float area = s * s;
    cout << "Area of Square = " << area << endl;
    return area;
}

float VolCyl() {
    float r, h;
    cout << "Enter radius: ";
    cin >> r;
    cout << "Enter height: ";
    cin >> h;
    float vol = 3.14 * r * r * h;
    cout << "Volume of Cylinder = " << vol << endl;
    return vol;
}

float VolS() {
    float r;
    cout << "Enter radius: ";
    cin >> r;
    float vol = (4.0 / 3.0) * 3.14 * r * r * r;
    cout << "Volume of Sphere = " << vol << endl;
    return vol;
}

int main() {
    while (true) {
        int ch;
        cout << "\nMenu:\n";
        cout << "1.Circle Area\n2.Rectangle Area\n3.Triangle Area\n4.Square Area\n";
        cout << "5.Cylinder Volume\n6.Sphere Volume\n7.Exit\n";
        cin >> ch;

        switch (ch) {
        case 1: AreaC(); break;
        case 2: AreaR(); break;
        case 3: AreaT(); break;
        case 4: AreaSq(); break;
        case 5: VolCyl(); break;
        case 6: VolS(); break;
        case 7: return 0;
        default: cout << "Invalid choice\n";
        }
    }
}
```

---

## Approach 3 – Object-Oriented Programming (OOP)

```cpp
#include <iostream>
using namespace std;

class Shape {
private:
    float area;

public:
    void areaCircle();
    void areaRectangle();
    void areaTriangle();
    void areaSquare();
    void volumeCylinder();
    void volumeSphere();
};

void Shape::areaCircle() {
    float r;
    cout << "Enter radius: ";
    cin >> r;
    area = 3.14 * r * r;
    cout << "Area of Circle = " << area << endl;
}

void Shape::areaTriangle() {
    float b, h;
    cout << "Enter base: ";
    cin >> b;
    cout << "Enter height: ";
    cin >> h;
    area = 0.5 * b * h;
    cout << "Area of Triangle = " << area << endl;
}

void Shape::areaSquare() {
    float s;
    cout << "Enter side: ";
    cin >> s;
    area = s * s;
    cout << "Area of Square = " << area << endl;
}

void Shape::volumeCylinder() {
    float r, h;
    cout << "Enter radius: ";
    cin >> r;
    cout << "Enter height: ";
    cin >> h;
    cout << "Volume of Cylinder = " << 3.14 * r * r * h << endl;
}

void Shape::volumeSphere() {
    float r;
    cout << "Enter radius: ";
    cin >> r;
    cout << "Volume of Sphere = " << (4.0 / 3.0) * 3.14 * r * r * r << endl;
}

void Shape::areaRectangle() {
    float l, w;
    cout << "Enter length: ";
    cin >> l;
    cout << "Enter width: ";
    cin >> w;
    area = l * w;
    cout << "Area of Rectangle = " << area << endl;
}

int main() {
    Shape s;
    int choice;

    while (1) {
        cout << "\nMenu:\n";
        cout << "1. Area of Circle\n";
        cout << "2. Area of Rectangle\n";
        cout << "3. Area of Triangle\n";
        cout << "4. Area of Square\n";
        cout << "5. Volume of Cylinder\n";
        cout << "6. Volume of Sphere\n";
        cout << "7. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
        case 1: s.areaCircle(); break;
        case 2: s.areaRectangle(); break;
        case 3: s.areaTriangle(); break;
        case 4: s.areaSquare(); break;
        case 5: s.volumeCylinder(); break;
        case 6: s.volumeSphere(); break;
        case 7: return 0;
        default: cout << "Invalid choice!" << endl;
        }
    }
}
```

---

## Comparison

| Aspect | Procedural | Object-Oriented |
|--------|-----------|-----------------|
| Code Structure | Functions/steps listed sequentially | Data and behaviour bundled in classes |
| Maintainability | Harder to extend; logic is scattered | Easier to extend; add new methods to the class |
| Reusability | Functions can be reused, but data is global/local | Objects encapsulate state; classes can be reused |
| Scalability | Becomes complex as program grows | Scales well with inheritance and polymorphism |

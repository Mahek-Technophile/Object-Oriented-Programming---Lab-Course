# Assignment 6 – File I/O: Student Information

## Problem Statement

Write a program that reads data (e.g., student information) from a text file and stores it in
objects. Implement functionality to write data from objects back to a text file.

---

## Key Concepts

### File Streams in C++
C++ provides the `<fstream>` header for file operations:

| Stream | Description |
|--------|-------------|
| `ofstream` | Output file stream — used to write to a file |
| `ifstream` | Input file stream — used to read from a file |
| `fstream` | File stream — supports both reading and writing |

### File Modes
| Mode | Description |
|------|-------------|
| `ios::in` | Open for reading |
| `ios::out` | Open for writing (truncates existing content) |
| `ios::app` | Open for writing (appends to existing content) |

---

## Code

```cpp
#include <iostream>
#include <fstream>
using namespace std;

class Student {
    //Data members (variables inside class)
    int rollNo;
    string name;
    float marks;

public:
    void input(int r, string n, float m) { 
        //Function to take values and store in object
        rollNo = r;
        name = n;
        marks = m;
    }

    void display() {
        //Function to print student data
        cout << rollNo << "\t" << name << "\t" << marks << endl;
    }

    void writeToFile(ofstream &fout) {
        // Function to write data into file | &fout = passed by reference
        fout << rollNo << " " << name << " " << marks << endl;

        //Writes data into file in the format: rollNo name marks
    }
};

int main() {
    Student s[10];

    ifstream fin;
    ofstream fout;

    fin.open("input.txt"); //Opens file for reading
    fout.open("output.txt"); // Opens file for writing

    if (!fin) {
        cout << "Error opening file";
        return 1;
    }

    int r, i = 0;
    float m;
    string n;

    // Read from file
    while (fin >> r >> n >> m) {  //Automatically stops at end of file
        s[i].input(r, n, m);
        i++;
    }

    fin.close();

    // Write + display
    for (int j = 0; j < i; j++) {
        s[j].writeToFile(fout);
        s[j].display();
    }

    fout.close();

    return 0;
}
```

---

## File Format (`students.txt`)

Each line in the file stores one student record:

```
1 Alice 88.5
2 Bob 76
3 Charlie 92.3
4 Diana 81
```

---

## Sample Output

```
Data written to students.txt successfully.

Reading student data from file:
Roll No: 1  Name: Alice  Marks: 88.5
Roll No: 2  Name: Bob  Marks: 76
Roll No: 3  Name: Charlie  Marks: 92.3
Roll No: 4  Name: Diana  Marks: 81
```

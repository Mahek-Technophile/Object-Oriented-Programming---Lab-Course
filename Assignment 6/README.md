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
#include <string>
using namespace std;

class Student {
public:
    int rollNo;
    string name;
    float marks;

    Student() : rollNo(0), name(""), marks(0.0f) {}

    Student(int r, string n, float m) : rollNo(r), name(n), marks(m) {}

    void display() const {
        cout << "Roll No: " << rollNo
             << "  Name: " << name
             << "  Marks: " << marks << endl;
    }
};

// Write student records to file
void writeToFile(const string& filename, Student students[], int size) {
    ofstream outFile(filename);
    if (!outFile) {
        cout << "Error opening file for writing!" << endl;
        return;
    }

    for (int i = 0; i < size; i++) {
        outFile << students[i].rollNo << " "
                << students[i].name << " "
                << students[i].marks << "\n";
    }

    outFile.close();
    cout << "Data written successfully.\n";
}

// Read student records from file
int readFromFile(const string& filename, Student students[]) {
    ifstream inFile(filename);
    if (!inFile) {
        cout << "Error opening file for reading!" << endl;
        return 0;
    }

    int count = 0;
    while (inFile >> students[count].rollNo
                  >> students[count].name
                  >> students[count].marks) {
        count++;
    }

    inFile.close();
    return count;
}

int main() {
    Student students[10];  // Array (max 10 students)

    // Initialize data
    students[0] = Student(1, "Alice", 88.5);
    students[1] = Student(2, "Bob", 76.0);
    students[2] = Student(3, "Charlie", 92.3);
    students[3] = Student(4, "Diana", 81.0);

    int size = 4;
    string filename = "students.txt";

    // Write to file
    writeToFile(filename, students, size);

    // Read from file
    Student loaded[10];
    int count = readFromFile(filename, loaded);

    cout << "\nReading student data:\n";
    for (int i = 0; i < count; i++) {
        loaded[i].display();
    }

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

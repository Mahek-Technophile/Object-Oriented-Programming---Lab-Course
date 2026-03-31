# Assignment 2 – Encapsulation: Bank Account Class

## Problem Statement

Design a class to represent a bank account with attributes (balance, account number) and methods
(deposit, withdraw) with proper access control (public, private, protected) to demonstrate
encapsulation.

---

## Key Concepts

### Access Specifiers

| Specifier | Description |
|-----------|-------------|
| `public` | Members are accessible from outside the class |
| `private` | Members are accessible only within the class |
| `protected` | Members are accessible within the class and its derived classes |

### Encapsulation

Encapsulation is the bundling of data (attributes) and methods (functions) that operate on the
data into a single unit (class), while restricting direct access to some of the object's
components. In this example, `accountNumber` and `balance` are `private` so they cannot be
modified directly from outside the class.

---

## Code

```cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    string accountNumber;
    double balance;

public:
    void initializeAccount() {
        cout << "Enter Account Number: ";
        cin >> accountNumber;
        cout << "Enter Initial Balance: ";
        cin >> balance;
        if (balance < 0) balance = 0;
    }

    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Deposited: " << amount << ". New Balance: " << balance << endl;
        }
    }

    void withdraw(double amount) {
        if (amount > balance) {
            cout << "Insufficient funds!" << endl;
        } else if (amount > 0) {
            balance -= amount;
            cout << "Withdrew: " << amount << ". New Balance: " << balance << endl;
        }
    }

    void display() {
        cout << "\n--- Account Details ---" << endl;
        cout << "Account: " << accountNumber << "\nBalance: " << balance << endl;
    }
};

int main() {
    BankAccount myAcc;
    int choice;
    double amt;

    cout << "Welcome to the Bank System" << endl;
    myAcc.initializeAccount();

    do {
        cout << "\n1. Deposit\n2. Withdraw\n3. Display\n4. Exit\nEnter Choice: ";
        cin >> choice;

        switch (choice) {
        case 1:
            cout << "Enter deposit amount: ";
            cin >> amt;
            myAcc.deposit(amt);
            break;
        case 2:
            cout << "Enter withdrawal amount: ";
            cin >> amt;
            myAcc.withdraw(amt);
            break;
        case 3:
            myAcc.display();
            break;
        case 4:
            cout << "Exiting..." << endl;
            break;
        default:
            cout << "Invalid choice!" << endl;
        }
    } while (choice != 4);

    return 0;
}
```

---

## Sample Output

```
Welcome to the Bank System
Enter Account Number: ACC12345
Enter Initial Balance: 1000

1. Deposit
2. Withdraw
3. Display
4. Exit
Enter Choice: 1
Enter deposit amount: 500
Deposited: 500. New Balance: 1500

Enter Choice: 2
Enter withdrawal amount: 200
Withdrew: 200. New Balance: 1300

Enter Choice: 3

--- Account Details ---
Account: ACC12345
Balance: 1300

Enter Choice: 4
Exiting...
```

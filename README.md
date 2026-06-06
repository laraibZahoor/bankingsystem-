# bankingsystem-
bankingsystem using C ++
Project Overview:

This project is a simple Bank Account Management System developed in C++ using Object-Oriented Programming (OOP) concepts. The system allows basic banking operations such as creating an account, depositing money, withdrawing money, and displaying account details.

The project demonstrates the practical implementation of classes, objects, constructors, vectors, and member functions in C++.

Objective:

The main objective of this project is to:

Understand Object-Oriented Programming concepts.
Implement classes and objects in C++.
Perform basic banking operations.
Manage account information efficiently.
Learn the use of vectors for storing multiple accounts.
Features
Create a bank account.
Deposit money into an account.
Withdraw money from an account.
Check available balance.
Display account information.
Prevent withdrawal when funds are insufficient.
Technologies Used
C++
Standard Template Library (STL)
Vector Container
Object-Oriented Programming (OOP)
Program Structure
Class: Account

The Account class stores account-related information and provides functions to perform banking operations.

Data Members
Variable	Description
name	Account holder's name
accNo	Account number
balance	Current account balance
Member Functions
Constructor
Account(string n, int a, float b)

Initializes account name, account number, and balance.

Deposit Function
void deposit(float amt)

Adds the specified amount to the account balance.

Withdraw Function
void withdraw(float amt)

Subtracts the specified amount from the balance if sufficient funds are available.

Display Function
void display()

Displays account details including account number, account holder name, and current balance.

How the Program Works
Step 1: Create Account

The program creates an account object and stores it in a vector.

Example:

accounts.push_back(Account("laraibzahoor", 01, 6000));
Step 2: Deposit Money

The deposit function increases the account balance.

Example:

accounts[0].deposit(2000);
Step 3: Withdraw Money

The withdraw function decreases the balance if sufficient funds are available.

Example:

accounts[0].withdraw(1000);
Step 4: Display Account Details

The display function shows complete account information.

Example:

accounts[0].display();
Sample Output
Account No: 1
Name: laraibzahoor
Balance: 7000
Calculation
Initial Balance = 6000
Deposit = 2000
New Balance = 8000

Withdraw = 1000
Final Balance = 7000
Compilation and Execution
Compile
g++ bank_management.cpp -o bank_management
Run
./bank_management

Advantages:

Simple and easy to understand.
Demonstrates OOP concepts effectively.
Efficient account management using classes.
Supports multiple accounts using vectors.
Easy to extend with additional features.

Limitations:

Data is not saved permanently.
No file handling or database support.
No user authentication system.
Limited banking operations.
Future Enhancements
Add account creation through user input.
Implement file handling for permanent storage.
Add login and authentication features.
Transfer money between accounts.
Interest calculation feature.
Transaction history management.
Graphical User Interface (GUI).

Conclusion:

The Bank Account Management System is a beginner-friendly C++ project that demonstrates the use of Object-Oriented Programming principles. It provides a simple simulation of banking operations such as deposits, withdrawals, and balance inquiries. The project serves as a foundation for developing more advanced banking applications with databases, authentication, and transaction management features.

Banking System (C++ OOP) - README
Project Overview

This is a simple Banking Management System developed in C++ using Object-Oriented Programming (OOP) concepts. The program allows users to create customer accounts, deposit and withdraw money, transfer funds between accounts, view account details, and check transaction history through a menu-driven interface.

Features
1. Create Customer
Create a new customer account.
Store:
Customer ID
Customer Name
Account Number
Initial Balance
2. Deposit Money
Deposit money into an existing account.
Balance is updated automatically.
Transaction is recorded in history.
3. Withdraw Money
Withdraw money from an account.
Prevents withdrawal if balance is insufficient.
Transaction is recorded in history.
4. Transfer Funds
Transfer money from one account to another.
Checks sender's balance before transfer.
Records transactions for both sender and receiver.
5. View Account Details
Display customer information:
Customer ID
Customer Name
Account Number
Current Balance
6. Transaction History
View all account transactions including:
Deposits
Withdrawals
Transfers Sent
Transfers Received
OOP Concepts Used
Class: Transaction

Stores transaction information.

Attributes

type → Transaction type
amount → Transaction amount
Class: Account

Manages account operations.

Attributes

accountNumber
balance
history

Functions

deposit()
withdraw()
transfer()
showTransactions()
getAccountNumber()
getBalance()
Class: Customer

Stores customer information.

Attributes

customerID
customerName
account

Functions

displayCustomer()
getCustomerID()
getCustomerName()
Program Menu
=====================================
         BANKING SYSTEM
=====================================
1. Create Customer
2. Deposit Money
3. Withdraw Money
4. Transfer Funds
5. View Account Details
6. View Transaction History
0. Exit

Enter Choice: 1

Customer ID: 01
Customer Name: Laraib Zahoor
Account Number: 2345
Initial Balance: 1000

Customer Created Successfully!


=====================================
         BANKING SYSTEM
=====================================
1. Create Customer
2. Deposit Money
3. Withdraw Money
4. Transfer Funds
5. View Account Details
6. View Transaction History
0. Exit

Enter Choice: 2

Enter Account Number: 2345
Enter Deposit Amount: 300

Amount Deposited Successfully.


=====================================
         BANKING SYSTEM
=====================================
1. Create Customer
2. Deposit Money
3. Withdraw Money
4. Transfer Funds
5. View Account Details
6. View Transaction History
0. Exit

Enter Choice: 3

Enter Account Number: 2345
Enter Withdrawal Amount: 100

Amount Withdrawn Successfully.


=====================================
         CUSTOMER DETAILS
=====================================

Customer ID    : 1
Customer Name  : Laraib Zahoor
Account Number : 2345
Balance        : Rs. 1200


=====================================
        TRANSACTION HISTORY
=====================================

Deposit             Rs. 300
Withdrawal          Rs. 100


=====================================
 Thank You For Using Banking System
=====================================

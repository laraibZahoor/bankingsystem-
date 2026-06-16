#include <iostream>
#include <vector>
#include <string>
#include <iomanip>

using namespace std;

class Transaction
{
public:
    string type;
    double amount;

    Transaction(string t, double a)
    {
        type = t;
        amount = a;
    }
};

class Account
{
private:
    int accountNumber;
    double balance;
    vector<Transaction> history;

public:
    Account(int accNo, double bal)
    {
        accountNumber = accNo;
        balance = bal;
    }

    int getAccountNumber()
    {
        return accountNumber;
    }

    double getBalance()
    {
        return balance;
    }

    void deposit(double amount)
    {
        balance += amount;
        history.push_back(Transaction("Deposit", amount));

        cout << "\nAmount Deposited Successfully.\n";
    }

    void withdraw(double amount)
    {
        if(amount > balance)
        {
            cout << "\nInsufficient Balance!\n";
            return;
        }

        balance -= amount;
        history.push_back(Transaction("Withdrawal", amount));

        cout << "\nAmount Withdrawn Successfully.\n";
    }

    void transfer(Account &receiver, double amount)
    {
        if(amount > balance)
        {
            cout << "\nInsufficient Balance!\n";
            return;
        }

        balance -= amount;
        receiver.balance += amount;

        history.push_back(Transaction("Transfer Sent", amount));
        receiver.history.push_back(Transaction("Transfer Received", amount));

        cout << "\nTransfer Successful.\n";
    }

    void showTransactions()
    {
        cout << "\n=====================================\n";
        cout << "        TRANSACTION HISTORY\n";
        cout << "=====================================\n";

        if(history.empty())
        {
            cout << "No Transactions Available.\n";
            return;
        }

        for(int i = 0; i < history.size(); i++)
        {
            cout << setw(20) << left << history[i].type
                 << " Rs. " << history[i].amount << endl;
        }
    }
};

class Customer
{
private:
    int customerID;
    string customerName;

public:
    Account *account;

    Customer(int id, string name,
             int accNo, double balance)
    {
        customerID = id;
        customerName = name;

        account = new Account(accNo, balance);
    }

    int getCustomerID()
    {
        return customerID;
    }

    string getCustomerName()
    {
        return customerName;
    }

    void displayCustomer()
    {
        cout << "\n=====================================\n";
        cout << "         CUSTOMER DETAILS\n";
        cout << "=====================================\n";

        cout << "Customer ID    : "
             << customerID << endl;

        cout << "Customer Name  : "
             << customerName << endl;

        cout << "Account Number : "
             << account->getAccountNumber() << endl;

        cout << "Balance        : Rs. "
             << account->getBalance() << endl;
    }
};

int main()
{
    vector<Customer*> customers;

    int choice;

    do
    {
        cout << "\n\n=====================================\n";
        cout << "         BANKING SYSTEM\n";
        cout << "=====================================\n";

        cout << "1. Create Customer\n";
        cout << "2. Deposit Money\n";
        cout << "3. Withdraw Money\n";
        cout << "4. Transfer Funds\n";
        cout << "5. View Account Details\n";
        cout << "6. View Transaction History\n";
        cout << "0. Exit\n";

        cout << "\nEnter Choice: ";
        cin >> choice;

        if(choice == 1)
        {
            int id, accNo;
            string name;
            double balance;

            cout << "\nCustomer ID: ";
            cin >> id;

            cin.ignore();

            cout << "Customer Name: ";
            getline(cin, name);

            cout << "Account Number: ";
            cin >> accNo;

            cout << "Initial Balance: ";
            cin >> balance;

            customers.push_back(
                new Customer(id, name,
                             accNo, balance));

            cout << "\nCustomer Created Successfully!\n";
        }

        else if(choice == 2)
        {
            int accNo;
            double amount;

            cout << "Enter Account Number: ";
            cin >> accNo;

            cout << "Enter Deposit Amount: ";
            cin >> amount;

            bool found = false;

            for(int i = 0; i < customers.size(); i++)
            {
                if(customers[i]->account->
                   getAccountNumber() == accNo)
                {
                    customers[i]->account->
                    deposit(amount);

                    found = true;
                }
            }

            if(!found)
                cout << "Account Not Found!\n";
        }

        else if(choice == 3)
        {
            int accNo;
            double amount;

            cout << "Enter Account Number: ";
            cin >> accNo;

            cout << "Enter Withdrawal Amount: ";
            cin >> amount;

            bool found = false;

            for(int i = 0; i < customers.size(); i++)
            {
                if(customers[i]->account->
                   getAccountNumber() == accNo)
                {
                    customers[i]->account->
                    withdraw(amount);

                    found = true;
                }
            }

            if(!found)
                cout << "Account Not Found!\n";
        }

        else if(choice == 4)
        {
            int senderAcc, receiverAcc;
            double amount;

            cout << "Sender Account Number: ";
            cin >> senderAcc;

            cout << "Receiver Account Number: ";
            cin >> receiverAcc;

            cout << "Amount: ";
            cin >> amount;

            Account *sender = NULL;
            Account *receiver = NULL;

            for(int i = 0; i < customers.size(); i++)
            {
                if(customers[i]->account->
                   getAccountNumber() == senderAcc)
                {
                    sender = customers[i]->account;
                }

                if(customers[i]->account->
                   getAccountNumber() == receiverAcc)
                {
                    receiver = customers[i]->account;
                }
            }

            if(sender != NULL &&
               receiver != NULL)
            {
                sender->transfer(*receiver,
                                 amount);
            }
            else
            {
                cout << "Invalid Account Number!\n";
            }
        }

        else if(choice == 5)
        {
            int accNo;

            cout << "Enter Account Number: ";
            cin >> accNo;

            bool found = false;

            for(int i = 0; i < customers.size(); i++)
            {
                if(customers[i]->account->
                   getAccountNumber() == accNo)
                {
                    customers[i]->
                    displayCustomer();

                    found = true;
                }
            }

            if(!found)
                cout << "Account Not Found!\n";
        }

        else if(choice == 6)
        {
            int accNo;

            cout << "Enter Account Number: ";
            cin >> accNo;

            bool found = false;

            for(int i = 0; i < customers.size(); i++)
            {
                if(customers[i]->account->
                   getAccountNumber() == accNo)
                {
                    customers[i]->account->
                    showTransactions();

                    found = true;
                }
            }

            if(!found)
                cout << "Account Not Found!\n";
        }

    }while(choice != 0);

    cout << "\n=====================================\n";
    cout << " Thank You For Using Banking System ";
    cout << "\n=====================================\n";

    return 0;
}

#include <iostream>
#include <vector>
using namespace std;

class Account {
public:
    string name;
    int accNo;
    float balance;

    Account(string n, int a, float b) {
        name = n;
        accNo = a;
        balance = b;
    }

    void deposit(float amt) {
        balance += amt;
    }

    void withdraw(float amt) {
        if(amt <= balance)
            balance -= amt;
        else
            cout << "Insufficient balance\n";
    }

    void display() {
        cout << "\nAccount No: " << accNo;
        cout << "\nName: " << name;
        cout << "\nBalance: " << balance << endl;
    }
};

int main() {
    vector<Account> accounts;
    accounts.push_back(Account("laraibzahoor", 01, 6000));

    accounts[0].deposit(2000);
    accounts[0].withdraw(1000);
    accounts[0].display();

    return 0;
}



#include <iostream>
#include <string>
using namespace std;

int main()
{
    int balance = 1000;
    int attempts = 0;
    int pin = 0000;
    int choice;
    int AccountNumber;
    int amount;
    int it;
    bool isAuthenticated = false;

    cout << "Welcome to Prime Mobile Money System!" << endl;

    while (true) {
        cout << "Please enter your PIN: "<< endl;
        cin >> pin;

        if (pin == 0000) {
            isAuthenticated = true;
            break;
        }

        attempts++;

        if (attempts == 3) {
            cout << "Too many wrong attempts. The program will exit now." << endl;
            return 0;
        }

        cout << "Incorrect PIN. Please try again." << endl;
    }

    cout << "Authentication successful." << endl;

    while (true) {
        cout << endl << "Please choose an option: " << endl;
        cout << "1. Check balance" << endl;
        cout << "2. Reset/change PIN" << endl;
        cout << "3. Send money" << endl;
        cout << "4. Buy airtime " << endl;
        cout << "5. Exit" << endl;
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Your balance is: GHC " << balance << endl;
                break;

            case 2:
                cout << "Please enter your new PIN: " << endl;
                cin >> pin;
                cout << "Your PIN has been successfully changed." << endl;
                break;

            case 3:
                cout << "Please enter the receiver's account number: " << endl;
                cin >> AccountNumber;
                cout << "Please enter the amount to send: "<< endl;
                cin >> amount;
                cout << "Sending GHC" << amount <<endl;
                cout << "To " << AccountNumber << endl;
                if (amount <= balance) {
                    balance -= amount;
                    cout << "Transaction successful. Your new balance is: GHC " << balance << endl;
                } else {
                    cout << "Transaction failed. You have insufficient funds." << endl;
                }
                break;

            case 4:
                cout << "Please enter the amount for airtime : " << endl;
                cin >> amount;
                cout << "Receiver : " << endl;
                cin >> it;
                if (amount <= balance) {
                    balance -= amount;
                    cout << "Transaction successful. Your new balance is: " << balance << endl;
                } else {
                    cout << "Transaction failed. You have insufficient funds." << endl;
                }
                break;

            case 5:
                cout << "Thank you for using Prime Mobile Money System!" << endl;
                return 0;

            default:
                cout << "Invalid choice. Please try again." << endl;
                break;
        }
    }

    return 0;
}


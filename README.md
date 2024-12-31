#include <iostream>
#include <string>
using namespace std; 
const int MAX_PASSENGERS = 100; //limit in train
int serialNumbers[MAX_PASSENGERS];
string names[MAX_PASSENGERS];
string mobileNumbers[MAX_PASSENGERS];
string emails[MAX_PASSENGERS];
int trainNumbers[MAX_PASSENGERS];
int seatNumbers[MAX_PASSENGERS];
int currentSerialNumber = 1;
int passengerCount = 0;
// Function to add a passenger
void addPassenger() 
{
    if (passengerCount >= MAX_PASSENGERS) {
        cout << "Maximum passenger limit reached!\n";
        return;
    }
    serialNumbers[passengerCount] = currentSerialNumber++;
    cin.ignore(); 
    cout << "Enter passenger name: ";
    getline(cin, names[passengerCount]);
    cout << "Enter mobile number: ";
    getline(cin, mobileNumbers[passengerCount]);
    cout << "Enter email: ";
    getline(cin, emails[passengerCount]);
    cout << "Enter train number: ";
    cin >> trainNumbers[passengerCount];
    cout << "Enter seat number: ";
    cin >> seatNumbers[passengerCount];
    passengerCount++;
    cout << "Passenger added successfully! Serial Number: " << serialNumbers[passengerCount - 1] << endl;
}
// Function to display passenger details
void displayPassengerDetails(int Arslan) {
    cout << "Serial Number: " << serialNumbers[Arslan] << endl;
    cout << "Name: " << names[Arslan] << endl;
    cout << "Mobile Number: " << mobileNumbers[Arslan] << endl;
    cout << "Email: " << emails[Arslan] << endl;
    cout << "Train Number: " << trainNumbers[Arslan] << endl;
   cout << "Seat Number: " << seatNumbers[Arslan] << endl;
}
// Function to search for a passenger by serial number
void searchPassenger() {
    int serial;
    cout << "Enter serial number to search: ";
    cin >> serial; 
    for (int i = 0; i < passengerCount; ++i) {
        if (serialNumbers[i] == serial) {
            displayPassengerDetails(i); 
            return;
        }
    }
    cout << "Passenger not found.\n";
}
// Function to delete a passenger by serial number
void deletePassenger() {
    int serial;
    cout << "Enter serial number to delete: ";
    cin >> serial;
    for (int i = 0; i < passengerCount; ++i) {
        if (serialNumbers[i] == serial) {
            for (int j = i; j < passengerCount - 1; ++j) {
                serialNumbers[j] = serialNumbers[j + 1];
                names[j] = names[j + 1];
                mobileNumbers[j] = mobileNumbers[j + 1];
                emails[j] = emails[j + 1];
                trainNumbers[j] = trainNumbers[j + 1];
                seatNumbers[j] = seatNumbers[j + 1];
            }
            passengerCount--; //100-1===>99
            cout << "Passenger deleted successfully!\n";
            return;
        }
    }
    cout << "Passenger not found.\n";
}
int main() {
    int choice;   
        /*do while loop; 
    do{
        block of statements;
    }while(condition);
    */
   do { 
        cout << "\n>>>>>>A3 Railway Reservation System Menu<<<<<" << endl;
        cout << "1. Add Passenger" << endl;
        cout << "2. Search Passenger" << endl;
        cout << "3. Delete Passenger" << endl;
        cout << "4. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice; //1
        switch (choice) 
        {
            case 1:
                addPassenger();
                break;
            case 2:
                searchPassenger();
                break;
            case 3:
                deletePassenger();
                break;
            case 4:
                cout << "Exiting the program...\n";
                break;
            default:
                cout << "Invalid choice! Please try again.\n";
        }
    } while (choice != 4);

    return 0;
}

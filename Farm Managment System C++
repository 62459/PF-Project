#include <iostream>
#include <iomanip>
#include <string>
#include <cctype> 
using namespace std;
// Color codes for console styling
#define RESET "\033[0m"
#define RED "\033[31m"
#define BLUE "\033[34m"
#define GREEN "\033[32m"
#define YELLOW "\033[33m"
#define CYAN "\033[36m"
#define BOLD "\033[1m"

struct Crop {
    string name;
    string plantingDate;
    bool isHarvested;
};
struct Animal {
    string type;
    float weight;
    string vaccinationDate;
    string nextDueDate;
    string morningFeedingTime;
    string eveningFeedingTime;
};
struct Seed {
    string type;
    int availableGrams;
    int usedGrams;
};
struct Fertilizer {
    string type;
    int availableKilograms;
    int usedKilograms;
};
struct LivestockRecord {
    string operationType;
    double expenses;
    double income;
};
// Function prototypes
void addCrop(Crop crops[], int &count, int maxCrops);
void markHarvested(Crop crops[], int count);
void displayReport(Crop crops[], int count);
bool validateNamecrop(const string &name);
bool validateDatecrop(const string &date);

void addAnimal(Animal animals[], int &count);
void displayAnimals(Animal animals[], int count);
void clearScreen();
void pauseScreen();
bool validateName(string input);
bool validateDate(string input);
bool validateTime(string input);

void addSeed(Seed seeds[], int &seedCount);
void addFertilizer(Fertilizer fertilizers[], int &fertilizerCount);
void editSeed(Seed seeds[], int seedCount);
void editFertilizer(Fertilizer fertilizers[], int fertilizerCount);
void deleteSeed(Seed seeds[], int &seedCount);
void deleteFertilizer(Fertilizer fertilizers[], int &fertilizerCount);
void generateReport(const Seed seeds[], int seedCount, const Fertilizer fertilizers[], int fertilizerCount);

void addRecord(LivestockRecord records[], int &count);
void editRecord(LivestockRecord records[], int count);
void deleteRecord(LivestockRecord records[], int &count);
void viewFinancialReport(LivestockRecord records[], int count);
void displayMenu();
int getValidatedInteger();
double getValidatedDouble();

cropmanagment()
{
     const int MAX_CROPS = 100;
    Crop crops[MAX_CROPS];
    int cropCount = 0;
    int choice;
    do {
        clearScreen();
           cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tCrop Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << "\t\t1. Add Crop" << endl;
        cout << "\t\t2. Mark Crop as Harvested" << endl;
        cout << "\t\t3. Display Crop Report" << endl;
        cout << "\t\t4. Exit" << endl;
        cout << "\n\t\tEnter your choice: " << GREEN;
        cin >> choice;
        cout << RESET;

        // Handle invalid input
        if (cin.fail()) {
            cin.clear();
            cin.ignore(1000, '\n');
            cout << RED << "Invalid input! Please enter a valid number." << RESET << endl;
             cout << "\nPress Enter to continue...";
        cin.ignore();
        cin.get();
            continue;
        }

        // Menu actions
        if (choice == 1) {
            addCrop(crops, cropCount, MAX_CROPS);
        } else if (choice == 2) {
            markHarvested(crops, cropCount);
        } else if (choice == 3) {
            displayReport(crops, cropCount);
        } else if (choice == 4) {
            cout << YELLOW << "Exiting the program..." << RESET << endl;
        } else {
            cout << RED << "Invalid choice! Please try again." << RESET << endl;
        }

        pauseScreen();
    } while (choice != 4);

    return 0;  
}
// Function to add a crop
void addCrop(Crop crops[], int &count, int maxCrops) {
    clearScreen();
       cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tAdd Crops" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (count >= maxCrops) {
        cout << RED << "Maximum crop limit reached. Cannot add more crops." << RESET << endl;
        return;
    }
    Crop newCrop;
    cin.ignore(); // Clear input buffer

    // Validate crop name
    cout << GREEN << "Enter crop name (letters only): " << RESET;
    getline(cin, newCrop.name);
    if (!validateNamecrop(newCrop.name)) {
        cout << RED << "Invalid crop name! Only letters are allowed." << RESET << endl;
        return;
    }

    // Validate planting date
    cout << GREEN << "Enter planting date (DD/MM/YYYY): " << RESET;
    getline(cin, newCrop.plantingDate);
    if (!validateDatecrop(newCrop.plantingDate)) {
        cout << RED << "Invalid date format! Please use DD/MM/YYYY." << RESET << endl;
        return;
    }

    // Add crop
    newCrop.isHarvested = false;
    crops[count++] = newCrop;
    cout << GREEN << "Crop added successfully!" << RESET << endl;
}
// Function to mark a crop as harvested
void markHarvested(Crop crops[], int count) {
    clearScreen();
    if (count == 0) {
        cout << RED << "No crops available to mark as harvested." << RESET << endl;
        return;
    }

    string cropName;
    cin.ignore(); // Clear input buffer
    cout << GREEN << "Enter the name of the crop to mark as harvested: " << RESET;
    getline(cin, cropName);

    for (int i = 0; i < count; i++) {
        if (crops[i].name == cropName) {
            crops[i].isHarvested = true;
            cout << GREEN << "Crop marked as harvested successfully!" << RESET << endl;
            return;
        }
    }

    cout << RED << "Crop not found!" << RESET << endl;
}
// Function to display crop report
void displayReport(Crop crops[], int count) {
    clearScreen();
    if (count == 0) {
        cout << RED << "No crops to display." << RESET << endl;
        return;
    }
   cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tCrop Report" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    cout << left << setw(20) << "Crop Name"
         << setw(20) << "Planting Date"
         << setw(15) << "Status" << endl;
    cout << string(55, '-') << endl;

    for (int i = 0; i < count; i++) {
        cout << left << setw(20) << crops[i].name
             << setw(20) << crops[i].plantingDate
             << setw(15) << (crops[i].isHarvested ? "Harvested" : "Growing") << endl;
    }
    cout << string(55, '-') << endl;
}
// Validation function for crop name (letters only)
bool validateNamecrop(const string &name) {
    for (char c : name) {
        if (!isalpha(c) && !isspace(c)) {
            return false;
        }
    }
    return true;
}
// Validation function for planting date (format: DD/MM/YYYY)
bool validateDatecrop(const string &date) {
    if (date.length() != 10 || date[2] != '/' || date[5] != '/') {
        return false;
    }
    for (int i = 0; i < date.length(); i++) {
        if ((i != 2 && i != 5) && !isdigit(date[i])) {
            return false;
        }
    }
    return true;
}
livestockmanagment()
{const int MAX_ANIMALS = 100;
    Animal animals[MAX_ANIMALS];
    int count = 0;
    int choice;

    do {
        clearScreen();
           cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tLivestock Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << "1. Add Animal" << endl;
        cout << "2. Display Animals" << endl;
        cout << "3. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        if (cin.fail()) {
            cin.clear(); // Clear input error flag
            cin.ignore(100, '\n'); // Ignore invalid input
            cout << RED << "Invalid input! Please enter a number." << RESET << endl;
            pauseScreen();
            continue;
        }

        if (choice == 1) {
            addAnimal(animals, count);
        } else if (choice == 2) {
            displayAnimals(animals, count);
        } else if (choice == 3) {
            cout << RED << "Exiting the program..." << RESET << endl;
        } else {
            cout << YELLOW << "Invalid choice! Please try again." << RESET << endl;
        }
        pauseScreen();
    } while (choice != 3);

    return 0;
	 
}
void addAnimal(Animal animals[], int &count) {
	system("cls");
	   cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tAdd Animal Detail" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (count >= 100) {
        cout << RED << "Animal limit reached!" << RESET << endl;
        return;
    }
    string input;
    // Validate animal type
    do {
        cout << GREEN << "Enter animal type (letters only): " << RESET;
        cin >> input;
        if (!validateName(input)) {
            cout << RED << "Invalid input! Only letters are allowed." << RESET << endl;
        }
    } while (!validateName(input));
    animals[count].type = input;
    // Validate weight
    cout << GREEN << "Enter weight (kg): " << RESET;
    while (!(cin >> animals[count].weight) || animals[count].weight <= 0) {
        cin.clear(); // Clear input error flag
        cin.ignore(100, '\n'); // Ignore invalid input
        cout << RED << "Invalid input! Please enter a positive number." << RESET << endl;
    }
    // Validate vaccination date
    do {
        cout << GREEN << "Enter vaccination date (DD/MM/YYYY): " << RESET;
        cin >> input;
        if (!validateDate(input)) {
            cout << RED << "Invalid input! Please follow the format DD/MM/YYYY." << RESET << endl;
        }
    } while (!validateDate(input));
    animals[count].vaccinationDate = input;
    // Validate next due date
    do {
        cout << GREEN << "Enter next due date (DD/MM/YYYY): " << RESET;
        cin >> input;
        if (!validateDate(input)) {
            cout << RED << "Invalid input! Please follow the format DD/MM/YYYY." << RESET << endl;
        }
    } while (!validateDate(input));
    animals[count].nextDueDate = input;
    // Validate morning feeding time
    do {
        cout << GREEN << "Enter morning feeding time (HH:MM): " << RESET;
        cin >> input;
        if (!validateTime(input)) {
            cout << RED << "Invalid input! Please follow the format HH:MM." << RESET << endl;
        }
    } while (!validateTime(input));
    animals[count].morningFeedingTime = input;
    // Validate evening feeding time
    do {
        cout << GREEN << "Enter evening feeding time (HH:MM): " << RESET;
        cin >> input;
        if (!validateTime(input)) {
            cout << RED << "Invalid input! Please follow the format HH:MM." << RESET << endl;
        }
    } while (!validateTime(input));
    animals[count].eveningFeedingTime = input;

    count++;
    cout << GREEN << "Animal added successfully!" << RESET << endl;
}
void displayAnimals(Animal animals[], int count) {
	system("cls");
    if (count == 0) {
        cout << RED << "No animals to display!" << RESET << endl;
        return;
    }
   cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tAnimal Report" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    cout << left << setw(20) << "Animal Type"
         << setw(10) << "Weight"
         << setw(20) << "Vaccination Date"
         << setw(20) << "Next Due Date"
         << setw(20) << "Morning Feed Time"
         << setw(20) << "Evening Feed Time" << endl;
    cout << string(120, '-') << endl;

    for (int i = 0; i < count; i++) {
        cout << left << setw(20) << animals[i].type
             << setw(10) << animals[i].weight
             << setw(20) << animals[i].vaccinationDate
             << setw(20) << animals[i].nextDueDate
             << setw(20) << animals[i].morningFeedingTime
             << setw(20) << animals[i].eveningFeedingTime << endl;
    }
}
bool validateName(string input) {
    for (char c : input) {
        if (!isalpha(c)) {
            return false;
        }
    }
    return true;
}
bool validateDate(string input) {
    if (input.length() != 10 || input[2] != '/' || input[5] != '/') {
        return false;
    }
    for (int i = 0; i < input.length(); i++) {
        if (i != 2 && i != 5 && !isdigit(input[i])) {
            return false;
        }
    }
    return true;
}
bool validateTime(string input) {
    if (input.length() != 5 || input[2] != ':') {
        return false;
    }
    for (int i = 0; i < input.length(); i++) {
        if (i != 2 && !isdigit(input[i])) {
            return false;
        }
    }
    return true;
}
void clearScreen() {
    cout << "\033[2J\033[1;1H";
}
void pauseScreen() {
    cin.ignore(); 
    cout << "Press Enter to continue...";
    cin.get();
}
 inventorymanagment()
 { const int MAX_ITEMS = 50; // Maximum number of seeds and fertilizers
    Seed seeds[MAX_ITEMS];
    Fertilizer fertilizers[MAX_ITEMS];
    int seedCount = 0, fertilizerCount = 0; // Current count of seeds and fertilizers
    int choice;
    do {
        // Display the main menu
    	system("cls");
       	cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tInventory Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << "1. Seeds\n";
        cout << "2. Fertilizers\n";
        cout << "3. Generate Report\n";
        cout << "4. Exit\n";
        cout << YELLOW << "Enter your choice: " << RESET;
        cin >> choice;
        switch (choice) {
        case 1:
            // Seed-related menu
            int seedChoice;
            do {system("cls");
                  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tSeed Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
                cout << "1. Add Seed\n";
                cout << "2. Edit Seed\n";
                cout << "3. Delete Seed\n";
                cout << "4. Back to Main Menu\n";
                cout << YELLOW << "Enter your choice: " << RESET;
                cin >> seedChoice;
                switch (seedChoice) {
                case 1: addSeed(seeds, seedCount);break;
                case 2:editSeed(seeds, seedCount);break;
                case 3:deleteSeed(seeds, seedCount);break;
                case 4: break;
                default:cout << RED << "Invalid choice! Please try again.\n" << RESET;
                } } while (seedChoice != 4);
            break;
        case 2:
            // Fertilizer-related menu
            int fertilizerChoice;
            do { system("cls");
              cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tFertilizer Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
              
                cout << "1. Add Fertilizer\n";
                cout << "2. Edit Fertilizer\n";
                cout << "3. Delete Fertilizer\n";
                cout << "4. Back to Main Menu\n";
                cout << YELLOW << "Enter your choice: " << RESET;
                cin >> fertilizerChoice;
                switch (fertilizerChoice) {
                case 1:addFertilizer(fertilizers, fertilizerCount); break;
                case 2:editFertilizer(fertilizers, fertilizerCount);break;
                case 3:deleteFertilizer(fertilizers, fertilizerCount); break;
                case 4:break;
                default:cout << RED << "Invalid choice! Please try again.\n" << RESET;
                }} while (fertilizerChoice != 4);
            break;
        case 3:
            // Generate Report
            generateReport(seeds, seedCount, fertilizers, fertilizerCount);
            break;
        case 4:
            cout << GREEN << "Exiting program. Goodbye!\n" << RESET;
            break;
        default:
            cout << RED << "Invalid choice! Please try again.\n" << RESET;
        } } while (choice != 4);

    return 0;}
 	// Function to add seed data
void addSeed(Seed seeds[], int &seedCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\t  ADD SEEDS" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (seedCount >= 50) {
        cout << RED << "Seed inventory full!\n" << RESET;
        return;}
    cout << "Enter seed type: ";
    cin >> seeds[seedCount].type;
    cout << "Enter available grams: ";
    cin >> seeds[seedCount].availableGrams;
    cout << "Enter used grams: ";
    cin >> seeds[seedCount].usedGrams;
    seedCount++;
    cout << GREEN << "Seed added successfully!\n" << RESET;}
// Function to add fertilizer data
void addFertilizer(Fertilizer fertilizers[], int &fertilizerCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tADD FERTILIZER" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (fertilizerCount >= 50) {
        cout << RED << "Fertilizer inventory full!\n" << RESET;
        return;}
    cout << "Enter fertilizer type: ";
    cin >> fertilizers[fertilizerCount].type;
    cout << "Enter available kilograms: ";
    cin >> fertilizers[fertilizerCount].availableKilograms;
    cout << "Enter used kilograms: ";
    cin >> fertilizers[fertilizerCount].usedKilograms;
    fertilizerCount++;
    cout << GREEN << "Fertilizer added successfully!\n" << RESET;}
// Function to edit seed data
void editSeed(Seed seeds[], int seedCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tEDIT SEEDS DATA" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (seedCount == 0) {
        cout << RED << "No seeds to edit!\n" << RESET;
        return; }
    int index;
    cout << "Enter seed index to edit (1-" << seedCount << "): ";
    cin >> index;
    if (index < 1 || index > seedCount) {
        cout << RED << "Invalid index!\n" << RESET;
        return;  }
    index--; // Convert to 0-based index
    cout << "Editing seed: " << seeds[index].type << "\n";
    cout << "Enter new available grams: ";
    cin >> seeds[index].availableGrams;
    cout << "Enter new used grams: ";
    cin >> seeds[index].usedGrams;
    cout << GREEN << "Seed edited successfully!\n" << RESET;}
// Function to edit fertilizer data
void editFertilizer(Fertilizer fertilizers[], int fertilizerCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tEdit fertilizer" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (fertilizerCount == 0) {
        cout << RED << "No fertilizers to edit!\n" << RESET;
        return; }
    int index;
    cout << "Enter fertilizer index to edit (1-" << fertilizerCount << "): ";
    cin >> index;
    if (index < 1 || index > fertilizerCount) {
        cout << RED << "Invalid index!\n" << RESET;
        return;  }
    index--; // Convert to 0-based index
    cout << "Editing fertilizer: " << fertilizers[index].type << "\n";
    cout << "Enter new available kilograms: ";
    cin >> fertilizers[index].availableKilograms;
    cout << "Enter new used kilograms: ";
    cin >> fertilizers[index].usedKilograms;
    cout << GREEN << "Fertilizer edited successfully!\n" << RESET;}
// Function to delete seed data
void deleteSeed(Seed seeds[], int &seedCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tDelete seeds" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (seedCount == 0) {
        cout << RED << "No seeds to delete!\n" << RESET;
        return; }
    int index;
    cout << "Enter seed index to delete (1-" << seedCount << "): ";
    cin >> index;
    if (index < 1 || index > seedCount) {
        cout << RED << "Invalid index!\n" << RESET;
        return;  }
    index--; // Convert to 0-based index
    for (int i = index; i < seedCount - 1; i++) {
        seeds[i] = seeds[i + 1];  }
    seedCount--;
    cout << GREEN << "Seed deleted successfully!\n" << RESET;}
// Function to delete fertilizer data
void deleteFertilizer(Fertilizer fertilizers[], int &fertilizerCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tDelete Fertilizer" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (fertilizerCount == 0) {
        cout << RED << "No fertilizers to delete!\n" << RESET;
        return; }
    int index;
    cout << "Enter fertilizer index to delete (1-" << fertilizerCount << "): ";
    cin >> index;
    if (index < 1 || index > fertilizerCount) {
        cout << RED << "Invalid index!\n" << RESET;
        return; }
    index--; // Convert to 0-based index
    for (int i = index; i < fertilizerCount - 1; i++) {
        fertilizers[i] = fertilizers[i + 1];
    }
    fertilizerCount--;
    cout << GREEN << "Fertilizer deleted successfully!\n" << RESET;
}
// Function to check alerts for low inventory
void checkAlerts(const Seed seeds[], int seedCount, const Fertilizer fertilizers[], int fertilizerCount) {
    for (int i = 0; i < seedCount; i++) {
        if (seeds[i].availableGrams < 1) {
            cout << RED << "Alert: Seed inventory for " << seeds[i].type << " is below 1 gram!" << RESET << endl;
        }  }
    for (int i = 0; i < fertilizerCount; i++) {
        if (fertilizers[i].availableKilograms < 2) {
            cout << RED << "Alert: Fertilizer inventory for " << fertilizers[i].type << " is below 2 kg!" << RESET << endl;
        }   }}
// Function to generate a report
void generateReport(const Seed seeds[], int seedCount, const Fertilizer fertilizers[], int fertilizerCount) {
	system("cls");
	  cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tSeed Inventory Report" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    cout << left << setw(15) << "Seed Type" 
         << setw(15) << "Available (grams)" 
         << setw(15) << "Used (grams)" << endl;
    cout << string(45, '-') << endl;
    for (int i = 0; i < seedCount; i++) {
        cout << left << setw(15) << seeds[i].type 
             << setw(15) << seeds[i].availableGrams 
             << setw(15) << seeds[i].usedGrams << endl;
    }
      cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tFertilizer Inventory Report" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    cout << left << setw(15) << "Fertilizer Type " 
         << setw(15) << "Available (kg) " 
         << setw(15) << "Used (kg)" << endl;
    cout << string(45, '-') << endl;
    for (int i = 0; i < fertilizerCount; i++) {
        cout << left << setw(15) << fertilizers[i].type 
             << setw(15) << fertilizers[i].availableKilograms 
             << setw(15) << fertilizers[i].usedKilograms << endl;   }
    cout << RESET;
    pauseScreen();
	}
 	 financialmanagment()
 	 {const int MAX_RECORDS = 100;
    LivestockRecord records[MAX_RECORDS];
    int count = 0;
    int choice;
    do {
        displayMenu();
        choice = getValidatedInteger();
        switch (choice) {
            case 1: addRecord(records, count); break;
            case 2: editRecord(records, count); break;
            case 3: deleteRecord(records, count); break;
            case 4: viewFinancialReport(records, count); break;
            case 5: cout << RED << "Exiting the program..." << RESET << endl; break;
            default: cout << YELLOW << "Invalid choice! Please try again." << RESET << endl; break;
        }
    } while (choice != 5);
    return 0;
	  }
	// Function to display the menu
void displayMenu() {
	system("cls");
      cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tFinancial Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    cout << "1. Add Record" << endl;
    cout << "2. Edit Record" << endl;
    cout << "3. Delete Record" << endl;
    cout << "4. View Financial Report" << endl;
    cout << "5. Exit" << endl;
    cout << "Enter your choice: ";
}
// Function to get validated integer input
int getValidatedInteger() {
    string input;
    int value;
    while (true) {
        cin >> input;
        bool isValid = true;
        // Validate if the input contains only digits
        for (char c : input) {
            if (!isdigit(c)) {
                isValid = false;
                break;
            } }
        if (isValid) {
            value = stoi(input); // Convert valid string to integer
            return value;
        } else {
            cout << RED << "Invalid input. " << GREEN << "Please enter a valid integer: " << RESET;
        }}}
// Function to get validated double input
double getValidatedDouble() {
    string input;
    double value;
    while (true) {
        cin >> input;
        bool isValid = true;
        bool decimalPointSeen = false;
        // Validate input for a valid floating-point number
        for (char c : input) {
            if (!isdigit(c)) {
                if (c == '.' && !decimalPointSeen) {
                    decimalPointSeen = true; // Allow one decimal point
                } else {
                    isValid = false;
                    break;
                }}  }
        if (isValid) {
            value = stod(input); // Convert valid string to double
            return value;
        } else {
            cout << RED << "Invalid input. " << GREEN << "Please enter a valid number: " << RESET;
        }}}
// Function to add a record
void addRecord(LivestockRecord records[], int &count) {
    system("cls");
       cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tAdd Record" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (count < 100) {
        cout << GREEN << "\tEnter operation type: " << RESET;
        cin >> records[count].operationType;
        cout << GREEN << "\tEnter expenses: " << RESET;
        records[count].expenses = getValidatedDouble();
        cout << GREEN << "\tEnter income: " << RESET;
        records[count].income = getValidatedDouble();
        count++;
        cout << GREEN << "\t\tRecord added successfully!" << RESET << endl;
    } else {
        cout << RED << "\t\tRecord limit reached!" << RESET << endl;
    }}
// Function to edit a record
void editRecord(LivestockRecord records[], int count) {
    system("cls");
       cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tEdit Record" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    int index;
    if (count == 0) {
        cout << YELLOW << "No records to edit." << RESET << endl;
        return;  }
    cout << GREEN << "Enter record index to edit (0 to " << count - 1 << "): " << RESET;
    index = getValidatedInteger();
    if (index >= 0 && index < count) {
        cout << GREEN << "\tEnter new operation type: " << RESET;
        cin >> records[index].operationType;
        cout << GREEN << "\tEnter new expenses: " << RESET;
        records[index].expenses = getValidatedDouble();
        cout << GREEN << "\tEnter new income: " << RESET;
        records[index].income = getValidatedDouble();
        cout << YELLOW<< "\t\tRecord updated successfully!" << RESET << endl;
    } else {
        cout << RED << "Invalid index!" << RESET << endl;
    }}
// Function to delete a record
void deleteRecord(LivestockRecord records[], int &count) {
    system("cls");
       cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tDelete Record" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    int index;
    if (count == 0) {
        cout << YELLOW << "\tNo records to delete." << RESET << endl;
        return;
    }
    cout << GREEN << "\tEnter record index to delete (0 to " << count - 1 << "): " << RESET;
    index = getValidatedInteger();
    if (index >= 0 && index < count) {
        for (int i = index; i < count - 1; i++) {
            records[i] = records[i + 1];
        }
        count--;
        cout << GREEN << "\tRecord deleted successfully!" << RESET << endl;
    } else {
        cout << RED << "\tInvalid index!" << RESET << endl;
    }}
// Function to view financial report
void viewFinancialReport(LivestockRecord records[], int count) {
system("cls");
   cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\t View Financial Report" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
    if (count == 0) {
        cout << YELLOW << "No records available." << RESET << endl;
        return;
    }
    double totalExpenses = 0, totalIncome = 0;
    cout << left << setw(20) << "Operation Type" 
         << setw(15) << "Expenses: " 
         << setw(15) << "Income: " << endl;
    for (int i = 0; i < count; i++) {
        cout << left << setw(20) << records[i].operationType 
             << setw(15) << records[i].expenses 
             << setw(15) << records[i].income << endl;
        totalExpenses += records[i].expenses;
        totalIncome += records[i].income;
    }
    cout << BLUE << "Total Expenses: " << RESET << totalExpenses << endl;
    cout << BLUE << "Total Income: " << RESET << totalIncome << endl;
    cout << BLUE << "Profit: " << RESET << totalIncome - totalExpenses << endl;
    pauseScreen();
    system("cls");
}
const int MAX_USERS = 100; 
string usernames[MAX_USERS];
string passwords[MAX_USERS];
int userCount = 0;
// Function to register a new user
void registerUser() {
    if (userCount >= MAX_USERS) {
        cout << RED << "User limit reached. Cannot register more users.\n" << RESET;
        return;
    }
    system("cls");
    string username, password;
    cout << CYAN << "==============================================" << RESET << endl;
    cout << BOLD << "\t\tREGISTER BELOW:" << RESET << endl;
    cout << CYAN << "==============================================" << RESET << endl;
    cout << "\tEnter username: ";
    cin >> username;
    for (int i = 0; i < userCount; i++) {
        if (usernames[i] == username) {
            cout << RED << "Username already exists. Please choose a different username.\n" << RESET;
            return;
        }
    }
    cout << "\tEnter password: ";
    cin >> password;

    usernames[userCount] = username;
    passwords[userCount] = password;
    userCount++;
    cout << GREEN << "\nUser registered successfully!" << RESET << endl;
}
// Function to login with up to 3 attempts
bool loginUser() { 
    system("cls");
    string username, password;
    int attempts = 0;
    cout << CYAN << "==============================================" << RESET << endl;
    cout << BOLD << "\t\tLOGIN HERE:" << RESET << endl;
    cout << CYAN << "==============================================" << RESET << endl;
    while (attempts < 3) {
        cout << "\tEnter username: ";
        cin >> username;
        cout << "\tEnter password: ";
        cin >> password;
        for (int i = 0; i < userCount; i++) {
            if (usernames[i] == username && passwords[i] == password) {
                cout << GREEN << "\t\tLogin successful!" << RESET << endl;
                return true;
            }}
        attempts++;
        cout << YELLOW << "Invalid credentials! Attempts remaining: " << 3 - attempts << RESET << endl;
    }
    cout << RED << "Login blocked after 3 failed attempts. Try again later.\n" << RESET;
    return false;
}
// Function to display post-login menu
void postLoginMenu() {
    int choice;
    do {
        system("cls");
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << BOLD << "\t\t\t POST LOGIN MENU" << RESET << endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << "\t\t\t1. Crop Management\n";
        cout << "\t\t\t2. Livestock Management\n";
        cout << "\t\t\t3. Inventory Management\n";
        cout << "\t\t\t4. Financial Management\n";
        cout << "\t\t\t5. Logout\n";
        cout << "\n\t\t Please enter your choice: ";
        cin >> choice;
        switch (choice) {
            case 1:
            	system("cls");
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << BOLD << "\t\t\tCrop Management " << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
                cropmanagment();  break;
            case 2:
            	system("cls");
        cout << CYAN << "\t\t===================================" << RESET << endl;
        cout << GREEN << "\t\t\tLivestock Management" << RESET<<endl;
        cout << CYAN << "\t\t===================================" << RESET << endl;
               livestockmanagment();
                
                break;
            case 3:
            system("cls");
                inventorymanagment();
                break;
            case 4:
            	system("cls");
                financialmanagment();
                break;
            case 5:
        cout << RED << "Logging out...\n" << RESET;
                return;
            default:
        cout << RED << "Invalid choice. Please try again.\n" << RESET;
        }
        cout << "\nPress Enter to continue...";
        cin.ignore();
        cin.get();
    } while (choice != 5);
}
// Function to change the password
void changePassword() {
    system("cls");
    string username, oldPassword, newPassword;
    cout << CYAN << "=========================================================================" << RESET << endl;
    cout << BOLD << "\t\t\tCHANGE PASSWORD" << RESET << endl;
    cout << CYAN << "=========================================================================" << RESET << endl;
    cout << "\nEnter username: ";
    cin >> username;
    cout << "Enter old password: ";
    cin >> oldPassword;
    for (int i = 0; i < userCount; i++) {
        if (usernames[i] == username && passwords[i] == oldPassword) {
            cout << "Enter new password: ";
            cin >> newPassword;
            passwords[i] = newPassword;
            cout << GREEN << "\nPassword changed successfully!" << RESET << endl;
            return;
        }
    }
    cout << RED << "\nInvalid credentials! Could not change password.\n" << RESET;
}
int main() {
    int choice;
    do { 	
        system("cls");
        cout << CYAN << "\t\t---------------------------------------" << RESET << endl;
        cout << BOLD << "\t\t         WELCOME DEAR USER!            " << RESET << endl;
        cout << CYAN << "\t\t______________  MENU  _________________" << RESET << endl;
        cout << "\t\t\t| " << GREEN << "1.  Register" << RESET << "         |" << endl;
        cout << "\t\t\t| " << GREEN << "2.  Login" << RESET << "         |" << endl;
        cout << "\t\t\t| " << GREEN << "3.  Change Password" << RESET << " |" << endl;
        cout << "\t\t\t| " << GREEN << "4.  Exit" << RESET << "         |" << endl;
        cout << "\n\t\t Please enter your choice: ";
        cin >> choice;
        switch (choice) {
            case 1: registerUser(); break;
            case 2: 
                if (loginUser()) {
                    postLoginMenu();
                }
                break;
            case 3: changePassword(); break;
            case 4: cout << RED << "Exiting...\n" << RESET; break;
            default: cout << RED << "Invalid choice! Try again.\n" << RESET;
        }

        if (choice != 4) {
            cout << "\nPress Enter to continue...";
            cin.ignore();
            cin.get();
        }
    } while (choice != 4);

    return 0;
}

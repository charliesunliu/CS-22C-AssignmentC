/* CS-22C-AssignmentC
For homework */
#include "stdafx.h"
#include <iostream>
#include <string>
#include <cmath>
#include <iomanip>
#include <fstream>
#include <limits.h>
using namespace std;

class Car
{
public:
	void setUp(string reportingMark, int carNumber, string kind, bool loaded, string destination);
	void outPut();

private:
	string reportingMark;
	int carNumber;
	string kind;
	bool loaded;
	string destination = "NONE";

};

void input(string&reportingMark, int &carNumber, string&kind, bool&loaded, string&destination);

int main()
{
	Car *ptr;
	ptr = new Car;
	string reportingMark;
	int carNumber;
	string kind;
	bool loaded;
	string destination = "NONE";
	input(reportingMark, carNumber, kind, loaded, destination);
	(*ptr).setUp(reportingMark, carNumber, kind, loaded, destination);
	(*ptr).outPut();
	delete []ptr;
	return 0;
}

void input(string&reportingMark, int &carNumber, string&kind, bool&loaded, string&destination)
{
	// What if the user enter numbers ?????????????????????????????????
	cout << "Please enter 2 to 4 upper case character for reportmarking: ";
	cin >> reportingMark;
	for (int i = 0; reportingMark[i]; i++)
	{
		reportingMark[i] = toupper(reportingMark[i]);
	}
	// what if they dont enter numbers ????????
	cout << "Please enter the number of the car: ";
	cin >> carNumber;
	int selection;
	cout << "Please choose a number for kind, 1 is business, 2 is maintenance, 3 is other.\n";
	cin >> selection;
	switch (selection)
	{
		case 1:
			kind = "business";
			break;
		case 2:
			kind = "maintenace";
			break;
		case 3:
			kind = "other";
			break;
		default:
			cout << "Please enter number 1, 2 or 3 !\n";
			cout << "Please choose a number for kind, 1 is business, 2 is maintenance, 3 is other.\n";
			cin >> selection;
	}
	cout << "Please enter if the car is loaded: ";
	cin >> loaded;
	cin.ignore();
	cout << "Please enter the destination of the car: ";
	getline(cin,destination);
	/*while (checkreportingMark == false)
	{
		cout << "Please enter 2 to 4 upper case character for reportmarking !";
		cin >> reportingMark;
		checkreportingMark = true;
		
			if (reportingMark[5] != '\0')
			{
				cout << "Please enter 2 to 4 upper characters !";
				checkreportingMark = false;
			}
		}
	}*/
}

void Car::setUp(string reportingMark1, int carNumber1, string kind1, bool loaded1, string destination1)
{
	reportingMark = reportingMark1;
	carNumber = carNumber1;
	kind = kind1;
	loaded = loaded1;
	destination = destination1;
}

void Car::outPut()
{
	cout << fixed << left << setw(18) << "reportingMark" << reportingMark << endl;
	cout << fixed << left << setw(18) << "carNumber" << carNumber << endl;
	cout << fixed << left << setw(18) << "kind" << kind << endl;
	cout << fixed << left << setw(18) << "loaded" << loaded << endl;
	cout << fixed << left << setw(18) << "destination" << destination << endl;
}

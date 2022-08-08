#include<iostream>
#include<string>
using namespace std;
struct carriages
{
	int carr_num;
	int carr_class;
	int carr_price;
	bool carr_seat[30];

};
int x;
carriages * n;
void menue_of_operations();
int exit();
void book_ticket();
void cancel_ticket();
void show_available_seats();
void print_profits();
int main()
{
	
	cout << "Enter the number of carriages in the train : ";
	cin >> x;
	n = new carriages[x];
	
	
	for (int i = 0; i <x; i++)
	{
		cout << "Carriage#" << i+1 << ":" << endl;
		cout << "Enter class: ";
		cin >> n[i].carr_class;
		cout << "Enter price: ";
		cin >> n[i].carr_price;
	}
	cout << "*****************************************" << endl;
	for (int i = 0; i < x; i++)
	{
		for (int j = 0; j < 30; j++)
		{
			n[i].carr_seat[j] = false;
		}
	}
	menue_of_operations();
	
	system("pause");
	return 0;
}
void menue_of_operations()
{
	int num;
	cout << "Enter 1 to book a ticket.\n";
	cout << "Enter 2 to cancel a ticket.\n";
	cout << "Enter 3 to show available seats.\n";
	cout << "Enter 4 to print  profits in detail.\n";
	cout << "Enter 0 to exit.\n";
	cout << "Your choice : ";
	cin >> num;
	cout << "*****************************************" << endl;
	if (num == 0)
	{
		exit();
	}
	if (num == 1)
	{
		book_ticket();
		
	}
	if (num == 2)
	{
		cancel_ticket();

	}
	if (num == 3)
	{
		show_available_seats();
		
	}
	if (num == 4)
	{

		print_profits();        
		
	}
}
int exit()
{
	return 0;
}
void book_ticket()
{
	int n_c,n_s;
	cout << "Enter the number of carriage : ";
	cin >> n_c;
	n_c -= 1;
	n[n_c].carr_num = n_c;
	cout << "Enter the number of seat : ";
	cin >> n_s;
	n_s -= 1;
	if (n[n_c].carr_seat[n_s] == true)
	{
		cout << "This seat is reserved , please enter another seat :" << endl;
	}
	else
	{
		n[n_c].carr_seat[n_s] = true;
		cout << "You have reserved the ticket successfully !!" << endl;
	}
	cout << "**********************************" << endl;
	 menue_of_operations();
}
void cancel_ticket()
{
	int n_c, n_s;
	cout << "Enter the number of carriage : ";
	cin >> n_c;
	n_c -= 1;
	n[n_c].carr_num = n_c;
	cout << "Enter the number of seat that you want to delete its reservation : ";
	cin >> n_s;
	n_s -= 1;
	if (n[n_c].carr_seat[n_s] == true)
	{
		n[n_c].carr_seat[n_s] = false;
		cout << "you have canceled the reservation successfully !!" << endl;
	}
	else
	{
		cout << "this seat is free ! ";
	}

	cout << "**********************************" << endl;
	menue_of_operations();
	
}
void show_available_seats()
{
	for (int i =0; i < x; i++)
	{
		cout << "The carriage  : " << i+1  << endl;
		for (int j = 0; j < 30; j++)
		{
			cout << "The seat " << j + 1 << " is "; 
			if (n[i].carr_seat[j] == true)
			{
				cout << "reserved " << endl;
			}
			else
			{
				cout << "free ! " << endl;
			}
		}
	}
	cout << "**********************************" << endl;
	menue_of_operations();
	
}
void print_profits()
{
	int sum ;
	for (int i = 0; i < x; i++)
	{
		sum = 0;
		cout << "The carriage  : " << i+1  << endl;
		for (int j = 0; j < 30; j++)
		{
			if (n[i].carr_seat[j])
			{
				sum += n[i].carr_price;

			}
		}
		cout << "The profits of this  carriage = " << sum << endl;		
	}
	menue_of_operations();
}
# Assignment
#include <iostream>
#include <fstream>
using namespace std;
void inputArray(int arr[], int size)
{
    cout<<"Enter"<<size<<"elements:\n";
    for (int i=0;i<size;i++)
    {
        cout<<"Element"<<i+1<<":";
        cin>>arr[i];
    }
}
void displayArray(int arr[],int size)
{
    cout<<"Array Elements:";
    for(int i=0;i<size;i++)
    {
        cout<<arr[i]<<" ";
    }
    cout<<endl;
}
int calculateSum(int arr[],int size)
{
    int sum = 0;
    for(int i=0; i<size;i++)
    {
        sum+=arr[i];
    }
    return sum;
}
void writeToFile(int arr[],int size)
{
    ofstream in("arrayData.txt");

    if(!in)
    {
        cout<<"Error opening file for writing!\n";
        return;
    }

    for(int i=0;i<size;i++)
    {
        in<<arr[i]<<" ";
    }

    in.close();
    cout<<"Data written to file successfully.\n";
}
void readFromFile(int arr[],int size)
{
    ifstream out("arrayData.txt");

    if (!out)
    {
        cout<<"Error opening file for reading!\n";
        return;
    }

    for(int i=0;i<size;i++)
    {
        out>>arr[i];
    }

    out.close();
    cout << "Data read from file successfully.\n";
}

int main()
{
     int SIZE = 10; 
    int arr[SIZE];
    inputArray(arr, SIZE);
    cout << "\nOriginal ";
    displayArray(arr, SIZE);
    int total = calculateSum(arr, SIZE);
    cout << "Sum of array elements: " << total << endl;
    writeToFile(arr, SIZE);
    for (int i = 0; i < SIZE; i++)
    {
        arr[i] = 0;
    }
    readFromFile(arr, SIZE);
    cout << "\nArray after reading from file:\n";
    displayArray(arr, SIZE);

    return 0;
}


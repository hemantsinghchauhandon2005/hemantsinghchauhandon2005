//Create a class Array_operations and include an array of numbers as data member of the class.
//
// Include get() and display() functions in class.
// Also include functions in class for performing the following operations:
//a) Find the largest number from the array.
//b) Insert an element in the array at the position entered by user.
//c) Delete an element in the array at the position entered by user
//Implement the class by creating a menu driven program to perform the above stated operations on array.
#include<iostream>
#include<stdlib.h>

#define SIZE 60

using namespace std;

class Array_operations
{
    int a[SIZE];
    int size;
    int largest;

public:
    Array_operations()
    {
        size = 0;
        largest = 0;
    }

    int retLargest()
    {
        return largest;
    }

    void get(int n)
    {
        size = n;
        for(int i =0; i<size; i++)
              cin>>a[i];
    }

    void display()
    {
        cout<<endl;
        for(int i =0; i<size; i++)
              cout<<a[i]<< " ";
    }


    int findLargest()
    {
        largest = a[0];
        int idx = 0,i;
        for(i =1; i<size; i++)
              {
                  if (largest<a[i])
                  {
                      largest = a[i];
                      idx = i;
                  }
              }
        return idx; // return index of largest element
    }

    void insert(int pos, int value)
    {

        if (size < SIZE)
        {
            for(int i = size-1; i>=pos; i--)
                a[i+1] = a[i];
            a[pos] = value;
            size++;

        }
        else
            cout<<"\n Array has no enough space to insert an element";

    }

     int Delete(int pos)
     {
         int deletedValue =a[pos];
         for (int i= pos; i<size; i++)
                a[i] = a[i+1];
         size--;
         return(deletedValue);
     }
};

int main()
{
    Array_operations ob1;
    int n,indx_largest,choice,pos,val;
    cout<<" Enter size of array: ";
    cin>>n;
    cout<<"populate Array: ";
    ob1.get(n);
    ob1.display();
    while(1)
    {
        cout<<"\n1 Find Largest";
        cout<<"\n2 Insertion";
        cout<<"\n3 Deletion";
        cout<<"\n4 Display";
        cout<<"\n5 Exit\n";
        cout<<"\n Enter your choice: ";
        cin>>choice;

       switch(choice)
        {
            case 1:   indx_largest = ob1.findLargest();
                      cout<<"\nLargest Element : "<<ob1.retLargest();
                      cout<<" at index: " <<indx_largest<<endl;
                      break;
            case 2:   cout<<"\n Enter the index where you want to insert: ";
                      cin>>pos;
                      cout<<"\n Enter the data ";
                      cin>>val;
                      ob1.insert(pos,val);
                      break;
            case 3:   cout<<"\n Enter the index where you want to delete: ";
                      cin>>pos;
                      cout<<"\n Deleted value: "<<ob1.Delete(pos);
                      break;

            case 4: ob1.display();
                    break;

            case 5: exit(0);


        } // end switch case

    } // end while

cout<< "\n Have a Nice day \n";
return 0;

 } // end main

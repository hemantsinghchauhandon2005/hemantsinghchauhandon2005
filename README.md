//Create a class Multiarray and include two-dimensional arrays as data members of the
//class. Include get() and display() function in class. Include functions in class to perform
//the operation of multiplication of two – 2D (two dimensional) arrays

#include<iostream>
#include<iomanip>
using namespace std;
class Multiarray
{
    int mat[10][10];
    int r,c;

public:
    void get(int arg1, int arg2)
    {
        int i,j;
        r = arg1;
        c = arg2;
        for(i = 0; i<r; i++)
            for(j = 0; j<c; j++)
                cin>>mat[i][j];
    }

    int getRows(){return r;}
    int getCols(){return c;}

    void display()
    {
     int i,j;
     for(i = 0; i<r; i++)
            {
                for(j = 0; j<c; j++)
                    cout<<setw(4)<<mat[i][j]<<" ";
                cout<<endl;
            }
    }

    Multiarray multiply(Multiarray ob)
    {
        Multiarray t;
        int i, j, k;
        t.r  = r;
        t.c = ob.c;

           for (i = 0; i < r; i++)
                {
                  for (j = 0; j < ob.c; j++)
                   {
                     t.mat[i][j] = 0;
                     for (k = 0; k < ob.r; k++)// col of invoking object
                       {
                         t.mat[i][j] = t.mat[i][j] + ((mat[i][k]) * (ob.mat[k][j]));
                       }// second inner
                   }// First Inner
                } // outer
           return t;
    }
};


int main()
{
    Multiarray m1, m2, m3;
    int row,col;
    cout<<" Enter rows and Columns for First Matrix";
    cout<<"\n Rows= "; cin>>row;
    cout<<"Cols= "; cin>>col;
    cout<<"\n Populate First Matrix\n";
    m1.get(row,col);

    cout<<" Enter rows and Columns for Second Matrix";
    cout<<"\n Rows= ";
    cin>>row;
    cout<<"Cols= ";
    cin>>col;
    cout<<"\n Populate Second Matrix\n";
    m2.get(row,col);

    if (m1.getCols() == m2.getRows())
    {
       m3 = m1.multiply(m2);
    }
    else
        {
            cout<<" \n Matrix Multiplication not possible due to wrong dimensions"
            return 0;


    cout<< "\nFirst Matrix\n";
    m1.display();

    cout<< "\nSecond Matrix\n";
    m2.display();

    cout<< "\nResultant Matrix\n";
    m3.display();
    return 0;
}

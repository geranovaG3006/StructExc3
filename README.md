# StructExc3
Да се напише програма, която създава структура Automobile с полета brand, model, date, и price, указващи марка, модел, дата на производство и цена на автомобилите в автосалон. Да се въведе цяло число n и след него n на брой данни от тип Automobile. Да се изведат всички налични автомобили, сортирани по цена.  

#include<iostream>
#include<cstring>
#include <iomanip>
using namespace std;
struct Automobile
{
    string brand;
    string model;
    string date;
    double price;
};
int main()
{
    int n;
    Automobile temp;
    cout<<"Number of cars: ";
    cin>>n;
    Automobile automobile[n];
    for(int i=0;i<n;i++)
    {
        cout<<"*****Automobile*****"<<i+1<<endl;
        cout<<"Brand: ";
        cin>>automobile[i].brand;
        cout<<"Model: ";
        cin.get();
        cin>>automobile[i].model;
        cout<<"Date: ";
        cin>>automobile[i].date;
        cout<<"price: ";
        cin>>automobile[i].price;
    }
    for(int i=0;i<n-1;i++)
    {
        for(int j=i+1;j<n;j++)
        {
            if(automobile[i].price>automobile[j].price)
            {
                temp=automobile[i];
                automobile[i]=automobile[j];
                automobile[j]=temp;
            }
        }
    }
    for(int i=0;i<n;i++)
    {
        cout<<"*****Automobile "<<i+1<<"*****"<<endl;
        cout<<"Brand: "<<automobile[i].brand<<endl;
        cout<<"Model: "<<automobile[i].model<<endl;
        cout<<"Date : "<<automobile[i].date<<endl;
        cout<<"Price: "<<automobile[i].price<<endl;
    }
    
    system("pause");
    return 0;
}

// Същата задача решена чрез указатели към структури
#include<iostream>
#include<cstring>
#include <iomanip>
using namespace std;
struct Automobile
{
    string brand;
    string model;
    string date;
    double price;
};
int main()
{
    int n;
    cout<<"Number of cars: ";
    cin>>n;
    Automobile automobile[n];
    Automobile *q_first;
    Automobile *q_next;
    q_first=automobile;
    q_next=automobile;
    for(int i=0;i<n;i++)
    {
            cout<<"Brand: ";
            cin>>q_first->brand;
            cout<<"Model: ";
            cin>>q_first->model;
            cout<<"Date: ";
            cin>>q_first->date;
            cout<<"Price: ";
            cin>>q_first->price;
            q_first++;
    }
    
    q_first=automobile;
    q_next=automobile;
    Automobile *temp;
    q_next++;
    
    for(int i=0;i<n;i++)
        {
            if(q_first->price<q_next->price)
            {
                temp=q_first;
                q_first=q_next;
                q_next=temp;
            }
            q_first++;
            q_next++;
        }
        
    q_first=automobile;
    q_next=automobile;
    for(int i=0;i<n;i++)
    {
        cout<<"*****Automobile "<<i+1<<"*****"<<endl;
        cout<<"Brand: "<<q_first->brand<<endl;
        cout<<"Model: "<<q_first->model<<endl;
        cout<<"Date : "<<q_first->date<<endl;
        cout<<"Price: "<<q_first->price<<endl;
        q_first++;
    }
    
    system("pause");
    return 0;
}

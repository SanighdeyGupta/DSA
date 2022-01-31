# ARRAYS AND FUNCTIONS

## PASSING BY REFRENCE

Array is not passed by value but it is always passed by refrence.

```C++
#include<iostream>

using namespace std;

void printarray(int arr[],int n){
    //cout<<"In function"<<sizeof(arr)<<endl; = 8[size of pointer]
    arr[0]=100; //changed both in main and function as passed by refrence;
    for(int i=0;i<n;i++){
        cout<<arr[i]<<", ";
    }
}

int main()
{
    int arr[] = {1,2,3,4,5,6};
    int n = sizeof(arr)/sizeof(int);
    //cout<<"In main"<<sizeof(arr)<<endl; = 24[size of arr]
    //required to pass n;
    printarray(arr,n);
    return 0;
}
```
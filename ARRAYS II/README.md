# INPUT/OUTPUT/UPDATE

If we don't innitialize the array, it will print garbage for all other values. Hence we should always innitialize it after decleration.

```C++
#include<iostream>

using namespace std;

int main()
{
    int marks[100] = {0};
    int n;
    cout<<"Enter the number of students: ";
    cin>>n;

    //Assign a value
    marks[0] = -1;

    //Input
    for(int i=1;i<=n;i++){
        cin>>marks[i];
    }

    //Update
    for(int i=1;i<=n;i++){
        marks[i] *= 2;
    }

    //Ouput
    for(int i=1;i<=n+5;i++){
        cout<<marks[i]<<", ";
    }
    return 0;
}
```
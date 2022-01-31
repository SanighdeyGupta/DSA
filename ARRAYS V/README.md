# REVERSING ARRAY

Array_reverse time complexity = O[n/2].

```C++
#include<iostream>

using namespace std;

void reverse_array(int arr[],int n){
    int s = 0;
    int e = n - 1;
    while (s<e)
    {
        swap(arr[s],arr[e]);
        s++;
        e--;
    }
    
}

int main()
{
    int arr[] = {10,20,30,45,55,60,80,90};
    int n = sizeof(arr)/sizeof(int);
    //output before function_call
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
    reverse_array(arr,n);
    //output after function_call
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
    return 0;
}
```
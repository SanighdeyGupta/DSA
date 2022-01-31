# PRINTING ARRAYS

## PRINTING PAIRS

Print_pairs time complexity = O[n].

```C++
#include<iostream>

using namespace std;

void print_all_pairs(int arr[],int n){
    //print all the elements
    for(int i=0;i<n;i++){
        int x = arr[i];
        for(int j=i+1;j<n;j++){    // j = 0;(all pairs)
            int y = arr[j];
            cout<<x<<", "<<y<<endl;
        }
        cout<<endl;
    }
}

int main()
{
    int arr[] = {10,20,30,40,50,60};
    int n = sizeof(arr)/sizeof(int);
    print_all_pairs(arr,n);
    return 0;
}
```

## PRINTING SUB-ARRAYS

Print_subsets time complexity = O[n^3].

```C++
#include<iostream>
using namespace std;

void print_subarrays(int arr[],int n){
    for(int i=0;i<n;i++){
        for(int j=i;j<n;j++){
            for(int k=i;k<=j;k++){
                cout<<arr[k]<<",";
            }
            cout<<endl;
        }
    }
    cout<<endl;
}

int main()
{
    int arr[] = {10,20,30,40,50,60};
    int n = sizeof(arr)/sizeof(int);
    print_subarrays(arr,n);
    return 0;
}
```
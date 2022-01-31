# PRINTING SUBARRAYS SUM

## BRUTE FORCE

Brute force method time complexity = O[n^3].

```C++
#include<iostream>
using namespace std;

int print_subarrays(int arr[],int n){
    int j = 0;
    int largest_sum = 0;
    for(int i=0;i<n;i++){
        for(int j=i;j<n;j++){
            int sum = 0;
            for(int k=i;k<=j;k++){
                sum += arr[k];
            }
            largest_sum = max(largest_sum,sum);
        }
    }
    return largest_sum;
}
```

## PREFIX METHOD


Prefix sum method time complexity = O[n^2].

```C++
int print_subarrays2(int arr[],int n){
    int prefix[n] = {0};
    prefix[0] = arr[0];
    for(int k=1;k<n;k++){
        prefix[k] = prefix[k-1] + arr[k];
    }

    int j = 0;
    int largest_sum = 0;
    for(int i=0;i<n;i++){
        for(int j=i;j<n;j++){
            int sum = i>0 ? prefix[j]-prefix[i-1] : prefix[j];
            largest_sum = max(largest_sum,sum);
        }
    }
    return largest_sum;
}
```

## KADANE'S ALGORITHM

Kadane sum method time complexity = O[n].

```C++
int print_subarrays3(int arr[],int n){
    int cs = 0;
    int largest = 0;
    for(int i=0;i<n;i++){
        cs += arr[i];
        if(cs<0){
            cs=0;
        }
        largest = max(largest,cs);
    }
    return largest;
}

int main()
{
    int arr[] = {10,20,30,40,50,60};
    int n = sizeof(arr)/sizeof(int);
    int index = print_subarrays(arr,n);
    int index2 = print_subarrays2(arr,n);
    int index3 = print_subarrays3(arr,n);
    cout<<index<<endl;
    cout<<index2<<endl;
    cout<<index3<<endl;
    return 0;
}
```
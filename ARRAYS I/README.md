# ARRAYS

## INTRODUCTION

An array is a collection of elements of the same type placed in contiguous memeory location.

![loading...](images/array.JPG)

```C++
#include<iostream>
#include<string>
using namespace std;

int main()
{
    int a[100];
    int a[100] = {0}; // initialise list -> array will be innitialised as 0 for all index
    int a[100] = {1,2,3}; // 1,2,3,0,0,0,0.....
    int a[] = {1,2,3}; // declare size=3 automatically
    string fruits[4] = {"apple","mango","guava"};
    return 0;
}
```

## INPUT/OUTPUT/UPDATE

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

## ARRAYS AND FUNCTIONS

### PASSING BY REFRENCE

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

## SEARCHING IN AN ARRAY

### LINEAR SEARCH

Linear_search has time complexity = O[n] and space complexity = O[1].

```C++
#include<iostream>

using namespace std;

int linear_search(int arr[],int n,int key){
    for(int i=0;i<n;i++){
        if(arr[i] == key){
            return i;
        }
    }
    return -1;
}

int main()
{
    int arr[] = {10,15,12,13,9,6,4,34,12,8};
    int n = sizeof(arr)/sizeof(int);
    int key;
    cin>>key;
    int index = linear_search(arr,n,key);
    if(index!=-1){
        cout<<key<<" is present at index "<<index<<endl;
    }
    else{
        cout<<key<<" is not found!!!"<<endl;
    }
    return 0;
}
```

### BINARY SEARCH

Binary_search has time complexity = O[log(n)base_2] and space complexity = O[1]. 

Search space must be monotonic(sorted).

```C++
#include<iostream>

using namespace std;

int binary_search(int arr[],int n,int key){
    //Implementation of binary search
    int s = 0;
    int e = n-1;
    while(s<=e){
        int mid = (s+e)/2;
        if(arr[mid] == key){
            return mid;
        }
        else if(arr[mid] > key){
            e = mid - 1;
        }
        else{
            s = mid - 1;
        }
    }
    return -1;
}

int main()
{
    int arr[] = {10,20,30,40,45,60,70,80};
    int n = sizeof(arr)/sizeof(int);
    int key;
    cout<<"Enter the element to be searched: ";
    cin>>key;
    int index = binary_search(arr,n,key);
    if(index!=-1){
        cout<<key<<" is present at index "<<index<<endl;
    }
    else{
        cout<<key<<" is not found!"<<endl;
    }
    return 0;
}
```

## REVERSING ARRAY

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

## PRINTING ARRAYS

### PRINTING PAIRS

Print_pairs time complexity = O[n^2].

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

### PRINTING SUB-ARRAYS

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

## PRINTING SUBARRAYS SUM

### BRUTE FORCE

Brute force method time complexity = O[n^3].

```C++
#include<iostream>
using namespace std;

int print_subarrays(int arr[],int n){
    int largest_sum = arr[0];
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

### PREFIX METHOD


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

### KADANE'S ALGORITHM

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

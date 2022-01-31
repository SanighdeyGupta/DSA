# SORTING

## BUBBLE SORTING

Take larger element to the end by repeatedly swapping the adjacent elements.

Bubble sort time complexity is O[n^2] and best is O[n].

```C++
#include<iostream>

using namespace std;

void bubble_sort(int arr[],int n){
    for(int i=1;i<=n-1;i++){
        for(int j=0;j<=(n-i)-1;j++){
            if(arr[j]>arr[j+1]){
                swap(arr[j],arr[j+1]);
            }
        }
    }
    for(int i=0;i<n;i++){
        cout<<arr[i]<<", ";
    }
}

void bubble_sort(int arr[],int n){
    int flag=0;
    for(int i=1;i<=n-1;i++){
        for(int j=0;j<=(n-i)-1;j++){
            if(arr[j]>arr[j+1]){
                swap(arr[j],arr[j+1]);
                flag=1;
            }
        }
        if(flag==0){
            break;
        }
    }
    for(int i=0;i<n;i++){
        cout<<arr[i]<<", ";
    }
}

int main()
{
    int arr[] = {-2,3,4,-1,5,-12,6,1,3};
    int n = sizeof(arr)/sizeof(int);
    bubble_sort(arr,n);
    return 0;
}
```

## INSERTION SORTING

Insertion sort is similar to playing caeds in our hands. It's just like inserting a card in it's correct position in a sorted part.

Insertion sort has time complexity O[n^2].

```C++
#include<iostream>
using namespace std;

void insertion_sort(int a[],int n){
    for(int i=1;i<=n-1;i++){
        int current = a[i];
        int prev = i-1;
        while(prev>=0 && a[prev]>current){
            a[prev+1] = a[prev];
            prev = prev - 1;
        }
        a[prev+1] = current;
    }
}

int main()
{
    int arr[] = {-2,3,4,-1,5,-12,6,1,3};
    int n = sizeof(arr)/sizeof(int);
    insertion_sort(arr,n);
    for(auto x : arr){
        cout<<x<<",";
    }
    return 0;
}
```

## SELECTION SORTING

Repeatedly find the mininmum element from unsorted part and putting it at the beginning.

Selection sort has time complexity = O[n^2].

```C++
#include<iostream>
using namespace std;

void selection_sort(int a[],int n){
    for(int pos=0;pos<=n-2;pos++){
        int current = a[pos];
        int min_pos = pos;
        //find out min element
        for(int j=pos;j<n;j++){
            if(a[j]<a[min_pos]){
                min_pos = j;
            }
        }
        //swapping
        swap(a[min_pos],a[pos]);
    }
}

int main()
{
    int arr[] = {-2,3,4,-1,5,-12,6,1,3};
    int n = sizeof(arr)/sizeof(int);
    selection_sort(arr,n);
    for(auto x : arr){
        cout<<x<<",";
    }
    return 0;
}
```

## INBUILT SORTING

Inbuilt sort has time complexity = O[nlogn].

```C++
#include<iostream>
#include<algorithm>
using namespace std;

bool compare(int a,int b){
    //cout<<"Comparing"<<a<<"and"<<b<<endl;
    return a<b;
}

int main()
{
    int arr[] = {10,9,8,6,5,4,3,2,11,16,8};
    int n = sizeof(arr)/sizeof(int);
    //sorting 
    sort(arr,arr+n,compare);
    //inbuilt
    //sort(arr,arr+n,greater<int>());
    //reverse the array
    //reverse(arr,arr+n);
    //print the output
    for (int i = 0; i < n; i++)
    {
        cout<<arr[i]<<",";
    }
    
    return 0;
}
```

## COUNTING SORTING

Counting sort has time complexity = O[range+n].

```C++
#include<iostream>
#include<vector>

using namespace std;

void counting_sort(int a[],int n){
    int largest = -1;
    for (int i = 0; i<n; i++)
    {
        largest = max(largest,a[i]);
    }
    //create a count array/vector
    vector<int> f(largest+1,0);
    //update the freq vector
    for (int i = 0; i < n; i++)
    {
        f[a[i]]++;
    }
    //put back the element from freq into original array
    int j = 0;
    for (int i = 0; i <= largest; i++)
    {
        while (f[i]>0)
        {
            a[j] = i;
            f[i]--;
            j++;
        }
    }
}

int main()
{
    int arr[] = {88,97,18,12,15,1,5,6,12,5,8};
    int n = sizeof(arr)/sizeof(int);
    counting_sort(arr,n);
    for (int i = 0; i < n; i++)
    {
        cout<<arr[i]<<",";
    }
    
    return 0;
}
```
# INTRODUCTION

* **Vectors** are **sequence containers** representing arrays that can change in size.
* Just like arrays, vectors use contiguous storage locations for their elements, which means that their **elements can also be accessed directly in O(1) time**.
* But unlike arrays, their **size can change dynamically**, with their storage being handled automatically by the container.
* **Vectors** can be used to create dynamic 1D and 2D **Arrays**.
* Unlike arrays, vector are **passed by value** to a function, you may can still pass them by refrence if it is required. 

```C++
#include<iostream>
#include<vector>

using namespace std;

int main()
{
    vector<int> arr = {1,2,10,12,15};
    //fill constructor(size,element);
    vector<int> v = {10,7};
    //push_back method
    arr.push_back(16);
    //pop_back
    arr.pop_back();
    //print all the elements
    for(int i=0;i<arr.size();i++){
        cout<<arr[i]<<endl;
    }
    //size of the vector(no. of elements)
    cout<<arr.size()<<endl;
    //capacity(underlying storage)
    cout<<arr.capacity()<<endl;
    return 0;
}
```
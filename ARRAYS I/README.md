# INTRODUCTION

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
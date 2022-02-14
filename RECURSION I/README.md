# RECURSION BASICS

*Recursion* in computer science is a technique where the solution to a problem depends on solution to *smaller instances of the same problem*.

**BASE CASE** => when we cannot move any further as we have already reached the value which will give us the final answer.

![loading...](images/rec1.JPG)

![loading...](images/rec2.JPG)

## EXAMPLE-1(Factorial)

* Time and space complexity = O[n].
* All recursive problems take extra space, becoz of the concept of implicit stack.

```C++
#include<iostream>
using namespace std;

int fact(int n){
    //base case
    if(n==0){
        return 1;
    }
    //rec case
    else{
        int ans = n*fact(n-1);
        return ans;
    }
}

int main()
{
    int n;
    cin>>;
    cout<<fact(n);
    return 0;
}
```

## EXAMPLE-2(Fibonacci series)

* Time complexity is O[2^n] and space complexity is O[n].

```C++
#include<iostream>
using namespace std;

int fib(int n){
    //basic case
    if(n==0 || n==1){
        return n;
    }
    //rec case
    int f1 = fib(n-1);
    int f2 = fib(n-2);
    return f1 + f2;
}

int main()
{
    int n;
    cin>>n;
    cout<<fib(n)<<endl;
    return 0;
}
```

## EXAMPLE-3(Sort check)

```C++
#include<iostream>
using namespace std;

bool issorted(int arr[],int n){
    //base case
    if(n==1 || n==0){
        return true;
    }
    //rec case
    if(arr[0]<arr[1] && issorted(arr+1,n-1)){
        return true;
    }
    return false;
}

bool issortedtwo(int arr[],int i,int n){
    //base case
    if(i==n-1){
        return true;
    }
    //rec case
    if(arr[i]<arr[i+1] && issortedtwo(arr,i+1,n)){
        return true;
    }
    return false
}

int main()
{
    int arr[] = {1,2,3,5,4,6};
    int n = sizeof(arr)/sizeof(int);
    cout<<issorted(arr,n);
    return 0;
}
```

## EXAMPLE-4(Print numbers)

```C++
#include<iostream>
using namespace std;

void dec(int n){
    //base case
    if(n==0){
        return;
    }
    //rec case;
    cout<<n<<",";
    dec(n-1};
}

void inc(int n){
    //base case
    if(n==0){
        return;
    }
    //rec case
    inc(n-1);
    cout<<n<<",";
}

int main()
{
    int n;
    cin>>n;
    dec(n);
    cout<<endl;
    inc(n);
    return 0;
}
```

## EXAMPLE-5(First occurence)

```C++
#include<iostream>
using namespace std;

int firstocc(int arr[],int n,int key){
    //base case
    if(n==0){
        return -1;
    }
    //rec case
    if(arr[0]==key){
        return 0;
    }
    int subindex = firstocc(arr+1,n-1,key);
    if(subindex!=1){
        return subindex + 1;
    }
    return -1;
}

int main()
{
    int arr[] = {1,3,5,7,6,2,11,21};
    int n = sizeof(arr)/sizeof(int);
    int key = 7;
    cout<<firstocc(arr,n,key)<<endl;
    return 0;
}
```

## EXAMPLE-6(Last occurence)

```C++
#include<iostream>
using namespace std;

int lastocc(int arr[],int n,int key){
    //base case
    if(n==0){
        return -1;
    }
    //rec case
    int subindex = lastocc(arr+1,n-1,key);
    if(subindex==-1){
        if(arr[0]==key){
        return 0;
    }
    else{
        return -1;
    }
    }
    else{
        return subindex + 1;
    }
}

int main()
{
    int arr[] = {1,3,5,7,6,2,11,21};
    int n = sizeof(arr)/sizeof(int);
    int key = 7;
    cout<<lastocc(arr,n,key)<<endl;
    return 0;
}
```
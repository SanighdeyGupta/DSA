# LINKED LIST

* Memory is created on the fly dynamically.

## BASIC OPERATIONS

```C++
#include<iostream>
using namespace std;

class list;

class node{
    int data;
    public:
    node* next;
    node(int d):data(d),next(NULL){}
    int getdata(){
        return data;
    }
    ~node(){
        if(next!=NULL){
            delete next;
        }
    }
    friend class list;
};

class list{
    node* head;
    node* tail;
    int helper(node* start,int key){
        //base case
        if(start==NULL){
            return -1;
        }
        //value matches
        if(start->data==key){
            return 0;
        }
        //remaining part of the linked list
        int subidx = helper(start->next,key);
        if(subidx==-1){
            return -1;
        }
        return subidx + 1;
    }
    public:
    list():head(NULL),tail(NULL){}
    node* begin(){
        return head;
    }
    void push_front(int data){
        if(head==NULL){
            node* n = new node(data);
            head = tail = n;
        }
        else{
            node* n = new node(data);
            n->next = head;
            head = n;
        }
    }
    void push_back(int data){
        if(head==NULL){
            node* n = new node(data);
            head = tail = n;
        }
        else{
            node* n = new node(data);
            tail->next = n;
            tail = n;
        }
    }
    void insert(int data,int pos){
        if(pos==0){
            push_front(data);
            return;
        }
        node* temp = head;
        for(int jump=1;jump<=(pos-1);jump++){
            temp = temp->next;
        }
        node* n = new node(data);
        n->next = temp->next;
        temp->next = n;
    }
    int search(int key){
        node* temp = head;
        int idx = 0;
        while(temp!=NULL){
            if(temp->data==key){
                return idx;
            }
            idx++;
            temp = temp->next;
        }
        return -1;
    }
    int recursivesearch(int key){
        int idx = helper(head,key);
        return idx;
    }
    void pop_front(){
        node* temp = head;
        head = head->next;
        temp->next = NULL;
        delete temp;
    }
    void pop_back(){
        node* temp = tail;
        tail = (tail-1);
        delete temp;
    }
    void reverse(node*&head){
        node* c = head;
        node* p = NULL;
        node*n;
        while(c!=NULL){
            //save the next node
            n = c->next;
            //make current node to point to prev
            c->next = p;
            //update p and c to take them 1 step forward
            p = c;
            c = n;
        }
        head =p;
    }
    ~list(){
        if(head!=NULL){
            delete head;
            head = NULL;
        }
    }
};

int main()
{
    list l;
    l.push_back(1);
    l.push_front(2);
    l.push_back(5);
    l.push_back(6);
    l.insert(2,2);
    l.pop_front();
    l.pop_back();
    node* head = l.begin();
    while(head != NULL){
        cout<<head->getdata()<<",";
        head = head->next;
    }
    int key;
    cin>>key;
    cout<<l.recursivesearch(key)<<endl;
    return 0;
```
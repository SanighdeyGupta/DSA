# TRIE DATA STRUCTURE

1. Generic tree like data structure.
2. Efficient information retrieval data structure.
3. Searches in optimal time O(key lenght) but uses extra storage.
4. Operations:-
* Inserting O[key length]
* Searching O[key length]
* Deletion O[key length]

## TRIE CLASS

1. Time complexity = O[N*lenght_of_word].
2. Space complexity = O[lenght_of_word].

```C++
#include<iostream>
#include<unordered_map>
#include<string>
using namespace std;

class Trie;

class Node{
    char data;
    unordered_map<char,Node*> m;
    bool isTerminal;
    public:
        Node(char d){
            data = d;
            isTerminal = false;
        }
        friend class Trie;
};
class Trie{
    Node* root;
    public:
        Trie(){
            root = new Node('\0');
        }

        //insertion
        void insert(string word){
            Node *temp = root;
            for(char ch : word){
                if(temp->m.count(ch)==0){
                    Node *n = new Node(ch);
                    temp->m[ch] = n;
                }
                temp = temp->m[ch];
            }
            temp->isTerminal = true;
        }
        //searching
        bool search(string word){
            Node* temp = root;
            for(char ch : word){
                if(temp->m.count(ch)==0){
                    return false;
                }
                temp = temp->m[ch];
            }
            return temp->isTerminal;
        }
};
int main()
{
    Trie t;
    string words[] = {"apple","hello","he","aple","news"};
    for(auto word : words){
        t.insert(word);
    }
    string key;
    cin>>key;
    cout<<t.search(key)<<endl;
    return 0;
}
```
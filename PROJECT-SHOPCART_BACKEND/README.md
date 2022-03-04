# SHOPPING_CART

## DATAMODEL

```C++
//product,item,cart
#include<string>
#include<unordered_map>
using namespace std;
//forward declaration
class item;
class Cart;

class Product{
private:  
    int id;
    string name;
    int price;
public:
    Product(){

    }
    Product(int u_id,string name,int price){
        id = u_id;
        this->name = name;
        this->price = price;
    }
    string getdisplayname(){
        return name + " : Rs " + to_string(price) + "\n";
    }
    string getshortname(){
        return name.substr(0,1);
    }
    friend class Item;
    friend class Cart;
};

class Item{
private:
    Product product;
    int quantitiy;
public:
    //constructor using a init list;
    Item(){

    }
    Item(Product p, int q):product(p), quantitiy(q){}
    int getItemprice(){
        return quantitiy*product.price;
    }
    string getItemInfo(){
        return to_string(quantitiy) + " x " + product.name + " Rs. " + to_string(quantitiy*product.price);
    }
    friend class Cart;
};

class Cart{
private:
    unordered_map<int,Item> item;
public:
    void addProduct(Product product){
        if(item.count(product.id)==0){
            Item newItem(product,1);
            item[product.id] = newItem;
        }
        else{
            item[product.id].quantitiy += 1;
        }    
    }
    int gettotal(){
        int total = 0;
        for(auto itempair : item){
            auto item = itempair.second;
            total += item.getItemprice();
        }
        return total;
    }
    string viewcart(){
        if(item.empty()){
            return "Cart is empty";
        }
        string itemizedlist;
        int cart_total = gettotal();
        for(auto itempair : item){
            auto items = itempair.second;
            itemizedlist.append(items.getItemInfo());
        }
        return itemizedlist + "\n Total Amount : Rs. " + to_string(cart_total) + "\n"; 
    }
    bool isEmpty(){
        return item.empty();
    }
};
```

## CART_MAIN

```C++
#include<iostream>
#include<vector>
#include"datamodel.h"
using namespace std;

vector<Product> allProducts = {
    Product{1,"apple",26},
    Product{3,"mango",16},
    Product{2,"guava",36},
    Product{5,"banana",56},
    Product{4,"strawberry",29},
    Product{6,"pineapple",20},
};

Product* chooseproduct(){
    //display list of products
    string productlist;
    cout<<"Available Products: "<<endl;
    for(auto product : allProducts){
        productlist.append(product.getdisplayname());
    }
    cout<<productlist<<endl;
    cout<<"---------------------"<<endl;
    string choice;
    cin>>choice;

    for(int i=0;i<allProducts.size();i++){
        if(allProducts[i].getshortname()==choice){
            return &allProducts[i];
        }
    }
    cout<<"Product not found!!!"<<endl;
    return NULL;
}

bool checkout(Cart &cart){
    if(cart.isEmpty()){
        return false;
    }
    int total = cart.gettotal();
    cout<<"Pay in cash";
    int paid;
    cin>>paid;
    if(paid>=total){
        cout<<"Change "<<paid-total<<endl;
        cout<<"Thankyou for shopping";
        return true;
    }
    else{
        cout<<"Not enough cash";
        return false;
    }
}

int main()
{
    char action;
    Cart cart;
    while(true){
        cout<<"Select an action - (a)dd Item, (v)iew Cart, (c)heckout"<<endl;
        cin>>action;
        if(action=='a'){
            ////add to cart
            Product* product = chooseproduct();
            if(product!=NULL){
                cout<<"Added to the cart "<<product->getdisplayname()<<endl;
                cart.addProduct(*product);
            }
        }
        else if(action=='v'){
            //view the cart
            cout<<"--------------"<<endl;
            cout<<cart.viewcart();
            cout<<"--------------"<<endl;
        }
        else if(action=='c'){
            //checkout
            cart.viewcart();
            if(checkout(cart)){
                break;
            }
        }
        else{
            cout<<"Please select an  appropriate option from the above"<<endl;
            continue;
        }
    }
    return 0;
}
```


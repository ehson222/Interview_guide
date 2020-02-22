# Interview_guide
FAAMG
```
//
//  LinkedList.hpp
//
//  Created by ehson Assani on 2/22/20.
//  Copyright © 2020 ehson Assani. All rights reserved.
//

#ifndef LinkedList_hpp
#define LinkedList_hpp

#include <stdio.h>
using namespace std;

struct node{
    int data;
    node* next;
    
    node() : data(0), next(nullptr) {}
};

class LinkedList{
public:
    LinkedList();
    ~LinkedList();
    void insertFront(int d);
    void insert(int pos, int d);
    void insertLast(int d);
    void removeData(int d);
    void display();
    
private:
    int capacity;
    node* head;
    void destroyList(node* leaf);
    void insertFront(node* leaf, int d);
    void insert(node* leaf, int pos, int d);
    void insertLast(node* leaf, int d);
    void removeData(node* leaf, int d);
    void display(node* leaf);
};

#endif /* LinkedList_hpp */

//
//  LinkedList.cpp
//
//  Created by ehson Assani on 2/22/20.
//  Copyright © 2020 ehson Assani. All rights reserved.
//

#include "LinkedList.hpp"
#include <iostream>

using namespace std;

LinkedList::LinkedList(): capacity(0), head(nullptr) {}

LinkedList::~LinkedList(){
    if(capacity){
        destroyList(head);
    } else{
        cout << "Empty LinkedList\n";
    }
}

void LinkedList::destroyList(node* leaf){
    while(leaf){
        node* temp = leaf;
        leaf = leaf->next;
        capacity--;
        delete temp;
    }
    head = nullptr;
}

void LinkedList::insertFront(int d){
    if(head){
        insertFront(head, d);
    } else{
        head = new node;
        head->data = d;
        head->next = nullptr;
        capacity++;
    }
}

void LinkedList::insertFront(node* leaf, int d){
    node* temp = new node;
    temp->data = d;
    temp->next = head;
    head = temp;
    capacity++;
}

void LinkedList::insert(int pos, int d){
    if(head && pos){
        insert(head, pos, d);
    } else{
        insertFront(d);
    }
}

void LinkedList::insert(node* leaf, int pos, int d){
    if(capacity < pos){
        insertLast(leaf, d);
    } else{
        node* slow = leaf;
        node* fast = leaf->next;
        int step = 1;
        
        while(step != pos){
            slow = fast;
            fast = fast->next;
            step++;
        }

        fast = new node;
        fast->data = d;
        fast->next = slow->next;
        slow->next = fast;
        capacity++;
    }
}

void LinkedList::insertLast(int d){
    if(head){
        insertLast(head, d);
    } else{
        head = new node;
        head->data = d;
        head->next = nullptr;
        capacity++;
    }
}

void LinkedList::insertLast(node* leaf, int d){
    node* trav = leaf;
    while(trav->next){
        trav = trav->next;
    }
    node* temp = new node;
    temp->data = d;
    temp->next = trav->next; // trav->next == nullptr
    trav->next = temp;
    capacity++;
}

void LinkedList::removeData(int d){
    if(head){
        removeData(head, d);
    }
}

void LinkedList::removeData(node* leaf, int d){
    if(leaf->data == d){
        node* temp = head;
        head = head->next;
        delete temp;
        capacity--;
    } else{
        node* slow = leaf;
        node* fast = leaf;
        while(fast && fast->data != d){
            slow = fast;
            fast = fast->next;
        }
        if(fast && fast->data == d){
            slow->next = fast->next;
            delete fast;
            capacity--;
        }
    }
}

void LinkedList::display(){
    if(capacity){
        display(head);
    } else{
        cout << "empty LinkedList\n";
    }
}

void LinkedList::display(node* leaf){
    node* temp = leaf;
    int reset = (capacity < 10) ? 3 : capacity % 10;
    int count = 0;
    while(temp){
        cout << temp->data << " ";
        if(++count == reset){
            cout << endl;
            count = 0;
        }
        temp = temp->next;
    }
    cout << endl;
}

//
int main(){
LinkedList* roots = new LinkedList();
    

    roots->insertFront(4);

    roots->removeData(4);

    roots->insert(3,3);

    roots->insertFront(2);
    roots->insert(0, 0);
    roots->insert(9, 9);
    roots->insert(3, 7);
    
    
    roots->removeData(3);
    
    roots->display();
    
    roots->~LinkedList();
    
    roots->display();
}
Output:
0 2 7 
9 
empty LinkedList
```

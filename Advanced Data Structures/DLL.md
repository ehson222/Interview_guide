# Interview_guide
FAAMG
```
//
//  DLL.hpp
//
//  Created by ehson Assani on 2/22/20.
//  Copyright © 2020 ehson Assani. All rights reserved.
//

#ifndef DLL_hpp
#define DLL_hpp

#include <stdio.h>
#include <iostream>

struct dnode{
    int data;
    dnode* prev;
    dnode* next;
    
    dnode() : data(0), prev(nullptr), next(nullptr){}
};

class DLL{
public:
    DLL();
    ~DLL();
    void insertFront(int d);
    void insert(int pos, int d);
    void insertLast(int d);
    void removeData(int d);
    void display();

private:
    int capacity;
    dnode *head, *tail;
    void destroyList(dnode* head);
    void insertFront(dnode* leaf, int d);
    void insert(dnode* leaf, int pos, int d);
    void insertLast(dnode* tail, int d);
    void removeData(dnode* head, int d);
    void display(dnode* head);
};
#endif /* DLL_hpp */

//
//  DLL.cpp
//
//  Created by ehson Assani on 2/22/20.
//  Copyright © 2020 ehson Assani. All rights reserved.
//

#include "DLL.hpp"
#include <iostream>
using namespace std;

DLL::DLL() : capacity(0), head(nullptr), tail(nullptr) {}

DLL::~DLL(){
    if(capacity){
        destroyList(head);
    } else{
        cout << "Empty DLL\n";
    }
}

void DLL::destroyList(dnode* front){
    while(front){
        dnode* temp = front;
        front = front->next;
        delete temp;
        capacity--;
    }
    head = tail = nullptr;
}

void DLL::insertFront(int d){
    if(capacity){
        insertFront(head, d);
    } else{
        dnode* temp = new dnode;
        temp->data = d;
        head = tail = temp;
        capacity++;
    }
}

void DLL::insertFront(dnode* front, int d){
    dnode* temp = new dnode;
    temp->data = d;
    temp->prev = nullptr;
    temp->next = front;
    
    front->prev = temp;
    head = temp;
    capacity++;
}

void DLL::insert(int pos, int d){
    if(capacity){
        insert(head, pos, d);
    } else{
        insertFront(d);
    }
}

void DLL::insert(dnode* front, int pos, int d){
    if(capacity < pos){
        insertLast(tail, d);
    } else{
        dnode* slow = front;
        dnode* fast = front->next;
        int step = 1;
        while(step != pos){
            slow = fast;
            fast = fast->next;
            step++;
        }
        dnode* temp = new dnode;
        temp->data = d;
        temp->prev = slow;
        temp->next = fast;
        slow->next = temp;
        fast->prev = temp;
        capacity++;
    }
}

void DLL::insertLast(int d){
    if(capacity){
        insertLast(tail, d);
    } else{
        insertFront(d);
    }
}

void DLL::insertLast(dnode* back, int d){
    dnode* temp = new dnode;
    temp->data = d;
    temp->prev = back;
    temp->next = nullptr;
    
    back->next = temp;
    tail = temp;
    capacity++;
}

void DLL::removeData(int d){
    if(capacity){
        removeData(head, d);
    }
}

void DLL::removeData(dnode* front, int d){
    if(head == tail && head->data == d){
        dnode* temp = head;
        head = head->next;
        tail = head;
        delete temp;
        capacity--;
    } else{
        dnode* slow = front;
        dnode* fast = front;
        while(fast && fast->data != d){
            slow = fast;
            fast = fast->next;
        }
        if(fast && fast->data == d){
            if(fast == tail){
                tail = tail->prev;
                delete fast;
                capacity--;
            } else if(slow == fast){
                head = head->next;
                head->prev = nullptr;
                delete fast;
                capacity--;
            } else{
                slow->next = fast->next;
                fast->next->prev = slow;
                delete fast;
                capacity--;
            }
        }
    }
    if(capacity == 0){
        head = tail = nullptr;
    }
}

void DLL::display(){
    if(capacity){
        display(head);
    } else{
        cout << "DLL empty\n";
    }
}


void DLL::display(dnode* front){
    dnode* temp = front;
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

int main(){
 DLL* doublyroot = new DLL();
    
    doublyroot->insertFront(5);
    doublyroot->insertLast(7);
    doublyroot->insert(1,6);
    
    doublyroot->insertFront(4);
    doublyroot->display();
    doublyroot->removeData(6);
    doublyroot->removeData(7);
    doublyroot->removeData(4);
    doublyroot->removeData(5);
    doublyroot->display();
    for(int i = 4; i > 0; --i){
        doublyroot->insertFront(i);
    }
    doublyroot->display();
    doublyroot->~DLL();
    doublyroot->display();
    
    return 0;
}

OUTPUT:

4 5 6 
7 
DLL empty
1 2 3 
4 
DLL empty

```

# Interview_guide
FAAMG
```
struct node{
int val;
node* next;
}

class LL{
public:
LL() : head(nullptr) {}
void insert(int x){
node* temp = head, trav = head;
while(temp->val < x){
trav = temp;
temp = temp->next;
}

node* change = new node;
change->next = temp;
trav->next = change;

}

private:
node* head;
}
```

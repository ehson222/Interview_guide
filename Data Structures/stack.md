# Interview_guide
FAAMG
```
class Stack{
private:
int* ptr;
int size;
int top;

public:
void push(int x);
int pop();
Stack();
Stack(int sz);
~Stack();
bool isempty();

};

Stack:: ~Stack(){
cout << " destructor of stack\n";
delete []ptr;
}

Stack:: Stack(){
cout << " Empty parameter constructor of stack\n";
ptr = new int[10];
top = -1;
}

Stack:: Stack(int sz){
cout << " One parameter constructor of stack\n";
size = sz;
ptr = new int[size];
top = -1;
}

void Stack:: push(int x){
if(top == size){
cout << " the stack is full, try popping the stack\n";
} else{
ptr[++top] = x;
}
}

int Stack:: pop(){
if(top == -1){
cout << " the stack is empty, try pushing to the stack\n";
}
return ptr[top--];
}

bool Stack:: isempty(){
if(top == -1){
return true;
} else{
return false;
}
}

void fun(){
Stack* sp = new Stack();
Stack* vp = new Stack(5);
for(int i = 1; i < 11; ++i){
sp->push(i);
}

for(int i = 1; i < 6; ++i){
vp->push(i);
}
while(!sp->isempty()){
cout << sp->pop() << " ";
}
cout << endl;
while(!vp->isempty()){
cout << vp->pop() << " ";
}
delete sp;
delete vp;
}
```

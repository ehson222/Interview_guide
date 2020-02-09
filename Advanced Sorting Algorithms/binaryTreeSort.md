# Interview_guide
FAAMG


```
struct treenode{
int val;
treenode *left;
treenode *right;
};

class btree{
public:
btree();
void insert(int data){
if(root){
insert(root, data);
} else{
root = new treenode;
root->val = data;
root->left = nullptr;
root->right = nullptr;
}
}
void inOrder(){
if(root){
inOrder(root);
}
}

private:
treenode *root;
void insert(treenode *leaf, int data){
if(leaf->val < data){
if(leaf->right){
insert(leaf->right, data);
} else{
leaf->right = new treenode;
leaf->right->val = data;
leaf->right->left = nullptr;
leaf->right->right = nullptr;
}
} else if(leaf->val >= data){
if(leaf->left){
insert(leaf->left, data);
} else{
leaf->left = new treenode;
leaf->left->val = data;
leaf->left->left = nullptr;
leaf->left->right = nullptr;
}
}
}
void inOrder(treenode* leaf){
stack<treenode*> ts;
treenode* trav = leaf;
cout << "printing inOrder:\n";
while(trav || !ts.empty()){
while(trav){
ts.push(trav);
trav = trav->left;
}
trav = ts.top();
ts.pop();
cout << trav->val << " ";
trav = trav->right;
}
cout << endl;
}
}

```

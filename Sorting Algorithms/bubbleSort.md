# Interview_guide
FAAMG
```
void bubbleSort(vector<int>& A){
if(A.size() < 2){
return;
}
for(int i = 0; i < A.size()-1; ++i){
for(int j = 0; j < A.size()-1; ++j){
if(A[j] > A[j+1]){
int temp = A[j];
A[j] = A[j+1];
A[j+1] = temp;
}
}
}
}

/
```

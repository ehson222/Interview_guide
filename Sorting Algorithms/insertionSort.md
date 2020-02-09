# Interview_guide
FAAMG

Best for 32 item or less list.
```
void insertionSort(vector<int>& A){
if(A.size() > 1){
for(int i = 1; i < A.size(); ++i){
for(int j = i; j > 0; --j){
if(A[j-1] > A[j]){
int temp = A[j-1];
A[j-1] = A[j];
A[j] = temp;
}
}
}
}
}
```

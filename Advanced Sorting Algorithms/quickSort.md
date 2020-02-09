# Interview_guide
FAAMG
```
void swapLH(vector<int>& A, int lo, int hi){
int temp = A[lo];
A[lo] = A[hi];
A[hi] = temp;
}

int partition(vector<int>& A, int i, int j){
int pivot = A[i];

int lo = i, hi = j-1;
while(lo < hi){
while(A[lo] <= pivot){
lo++;
}
while(A[hi] > pivot){
hi--;
}
if(A[lo] > A[hi] && lo < hi){
swapLH(A, lo, hi);
lo++, hi--;
}
}

swapLH(A, i, hi);
return hi;
}

void quickSort(vector<int>& A, int lo, int hi){
if(lo < hi){
int mid = partition(A, lo, hi);
quickSort(A, lo, mid);
quickSort(A, mid+1, hi);
}
}
```

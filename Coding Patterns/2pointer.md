# Interview_guide
FAAMG
A simple technique where you have a start pointer and an end pointer.  You iterate them towards each other and stop when start and end are pointing to same index.

```
bool isNumber(int x){
return (x >= 48 && x<= 57);
}

void swapNumbers(string& A){
for(int i = 0, j = A.size()-1; i < A.size()/2; ++i){
while(i < j && !isNumber(A[i])){
++i;
}
while(j > i && !isNumber(A[j])){
--j;
}
if(isNumber(A[i]) && isNumber(A[j])){
int temp = A[i];
A[i] = A[j];
A[j] = temp;
i++;
j--;
}
}
}
```

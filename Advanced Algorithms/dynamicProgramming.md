# Interview_guide
FAAMG

In-Depth:
To get our solution, we either have to use an auxillary array of size 1 + of our argument, or we can juggle a few variables and use constant space.  Most of the time we have to precompute our starting values/index(s) or our bottom-up solution will not work.  It is best if you draw out the steps on a paper or whiteboard to internalize the process.  In my opinion it is one of the most interesting algorithmic techniques I've encounterd and I always think can I do this with DP.


TLDR:
The key to DP is that we must always start from the bottom to get our answer.  Like the song, "started from the bottom".

```
// with aux array
int fib(int n){
vector<int> A(n+1, 0);
A[0] = 0;
A[1] = 1;
for(int i = 2; i < A.size(); ++i){
A[i] = A[i-1] + A[i-2];
}
return A[n];
}

// without aux array

int fib(int n){
int a = 0, b = 1, c = 0, k = 1;
while(k < n){
c = a + b;
a = b;
b = c;
k++;
}
return c;
}

```

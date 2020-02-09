# Interview_guide
FAAMG
while these basic problems below can be done with a for loop, it is good practice to understand what goes on in memory (the stack) with how these functions work.  Each time the function calls itself, it creates another stack frame.  

```
int factorial(int n){
if(n < 2){
return 1;
}
return n * factorial(n-1);
}


// TAIL RECURSION

void tail(int n){
if(n == 1) return;
cout << n << " ";
tail(n-1);
}

// HEAD RECURSION

void head(int n){
if(n==1) return;

head(n-1);

cout << n << " ";
}
```

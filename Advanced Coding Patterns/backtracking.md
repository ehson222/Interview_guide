# Interview_guide
FAAMG

The backtracking pattern is best used to finding all possible permutations of a problem or all possible moves of a knight.
IMO, this is a very powerful tool, and it takes a while to understand. You must be excellent at basics of recursion to tackle this programming paradigm.

```
following is pseudo code::

void dfs(int A[], int n){
if(base case){

}
else{
for(loop through array){
change array element;
dfs(A, i+1);
revert array element;
}
}
}
```

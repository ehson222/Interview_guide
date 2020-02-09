# Interview_guide
FAAMG

This originally started out as a way to test beginner programmers to find the largest or smallest element in array.  Then they were asked to find the 2nd largest or smallest.  Finally, the Kth largest was to be found in an array of size of a thousand.  The normal trick to get largest or smallest would not work for this, but a simple heap data structure is all we need.

We can also heapifyup to get solution to this problem instead of just inserting to heap.

```
int findKthLargest(vector<int>& nums, int k) {
if(nums.size() < 1){
return -1;
}
priority_queue<int, vector<int>, greater<int>> minHeap;

for(int i = 1; i < nums.size(); ++i){
minHeap.push(nums[i]);
if(minHeap.size() > k){
minHeap.pop();
}
}

return minHeap.top();

}
```

# Interview_guide
FAAMG
```
void merge(vector<int>& nums, int lo, int mid, int hi, vector<int>& aux){
int i = lo, j = mid+1, k = lo;
while(i <= mid && j <= hi){
if(nums[i] <= nums[j]){
aux[k++] = nums[i++];
} else{
aux[k++] = nums[j++];
}
}

while(i <= mid) aux[k++] = nums[i++];
while(j <= hi) aux[k++] = nums[j++];

while(lo < j){
nums[lo] = aux[lo];
lo++;
};
}

void mergeSort(vector<int>& nums, int lo, int hi, vector<int>& aux){
if(lo < hi){
int mid = ((unsigned int) lo + (unsigned int) hi) / 2;
mergeSort(nums, lo, mid, aux);
mergeSort(nums, mid+1, hi, aux);
merge(nums, lo, mid, hi, aux);
}
}

vector<int> sortArray(vector<int>& nums) {
vector<int> aux(nums.size(), 0);
mergeSort(nums, 0, nums.size()-1, aux);
return nums;
}

```

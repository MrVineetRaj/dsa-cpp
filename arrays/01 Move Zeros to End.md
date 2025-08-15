# Move Zeros to End

Given an integer array nums, move all the 0's to the end of the array. The relative order of the other elements must remain the same. This must be done in place, without making a copy of the array.

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int n = nums.size();
        int s = 0;
        int m = 0;

        while(m < n ){
            if(nums[m] != 0){
                swap(nums[m],nums[s]);
                s++;
                m++;
            }
            else if(nums[m] == 0){
                m++;
            }
        }
    }
};
```

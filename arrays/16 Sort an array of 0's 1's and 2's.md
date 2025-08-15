# Sort an array of 0's 1's and 2's

## Dutch National Flag algorithm

Given an array nums consisting of only 0, 1, or 2. Sort the array in non-decreasing order. The sorting must be done in-place, without making a copy of the original array.

```cpp
class Solution {
   public:
    void sortZeroOneTwo(vector<int>& nums) {
        int n = nums.size();
        int s = 0;
        int m = 0;
        int e = n - 1;

        while (m <= e) {
            if (nums[m] == 1) {
                m++;
            } else if (nums[m] == 0) {
                swap(nums[m++], nums[s++]);
            } else if (nums[m] == 2) {
                swap(nums[m], nums[e--]);
            }
        }
    }
};
```

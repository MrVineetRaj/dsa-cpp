# Rearrange array elements by sign

Given an integer array nums of even length consisting of an equal number of positive and negative integers.Return the answer array in such a way that the given conditions are met:

- Every consecutive pair of integers have opposite signs.
- For all integers with the same sign, the order in which they were present in nums is preserved.
- The rearranged array begins with a positive integer.

```cpp
class Solution {
   public:
    vector<int> rearrangeArray(vector<int>& nums) {

        int n = nums.size();
        vector<int> neg;
        vector<int> pos;

        for(int i = 0; i < n; i++){
            if(nums[i] < 0) neg.push_back(nums[i]);
            if(nums[i] > 0) pos.push_back(nums[i]);
        }

        int currNeg = 0;
        int currPos = 0;
        for(int i = 0; i < n; i++){
            if(i%2 == 0) nums[i] = pos[currPos++];
            else nums[i] = neg[currNeg++];
        }

        return nums;
    }
};
```

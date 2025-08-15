# Kadane's Algorithm

Given an integer array nums, find the subarray with the largest sum and return the sum of the elements present in that subarray.

A subarray is a contiguous non-empty sequence of elements within an array.

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxSum = INT_MIN;
        int sum = 0;
        for(int i = 0; i < nums.size();i++){
            sum+=nums[i];
            maxSum = max(maxSum,sum);

            if(sum < 0) sum = 0;
        }

        return maxSum;

    }
};
```

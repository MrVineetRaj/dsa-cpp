# Leaders in an Array

Given an integer array nums, return a list of all the leaders in the array.

A leader in an array is an element whose value is strictly greater than all elements to its right in the given array. The rightmost element is always a leader. The elements in the leader array must appear in the order they appear in the nums array.

```cpp
class Solution {
   public:
    vector<int> leaders(vector<int>& nums) {
        vector<int> result;
        int n = nums.size();
        int e = n - 1;
        int rightMax = INT_MIN;
        while(e >= 0){
            if(nums[e] > rightMax) result.push_back(nums[e]);
            rightMax= max(rightMax,nums[e]);
            e--;
        }

        reverse(result.begin(),result.end());

        return result;
    }
};
```

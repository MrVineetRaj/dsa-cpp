# Maximum Product Subarray in an Array

Given an integer array nums. Find the subarray with the largest product, and return the product of the elements present in that subarray.

A subarray is a contiguous non-empty sequence of elements within an array.

```cpp
class Solution {
   public:
    int maxProduct(vector<int>& nums) {
        int n = nums.size();
        int prefProduct = 1;
        int suffProduct = 1;
        int ans = INT_MIN;

        for (int i = 0; i < n; i++) {
            if(prefProduct == 0) prefProduct = 1;
            if(suffProduct == 0) suffProduct = 1;

            prefProduct*= nums[i];
            suffProduct*= nums[(n-1)-i];

            ans = max(ans,suffProduct);
            ans = max(ans,prefProduct);
        }
        return ans;
    }
};
```
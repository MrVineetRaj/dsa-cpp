# Two Sum

Given an array of integers nums and an integer target. Return the indices(0 - indexed) of two elements in nums such that they add up to target.

Each input will have exactly one solution, and the same element cannot be used twice. Return the answer in increasing order.

```cpp
class Solution {
   public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int> m;
        int n = nums.size();
        for (int i = 0; i < n; i++) {
            int rem = target - nums[i];
            if (m.find(rem) != m.end()) {
                return {m[rem], i};
            } else {
                m[nums[i]] = i;
            }
        }

        return {};
    }
};
```


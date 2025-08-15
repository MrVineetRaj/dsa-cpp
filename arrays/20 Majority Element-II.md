# Majority Element II

Given an integer array nums of size n. Return all elements which appear more than n/3 times in the array. The output can be returned in any order.

```cpp
class Solution {
   public:
    vector<int> majorityElementTwo(vector<int>& nums) {
        vector<int> cnt = {0, 0};
        vector<int> elem = {-1, -1};

        int n = nums.size();

        for (int i = 0; i < n; i++) {
            if (cnt[0] == 0 && nums[i] != elem[1]) {
                elem[0] = nums[i];
                cnt[0]++;
            } else if (cnt[1] == 0 && nums[i] != elem[0]) {
                elem[1] = nums[i];
                cnt[1]++;
            } else if (nums[i] == elem[0])
                cnt[0]++;
            else if (nums[i] == elem[1])
                cnt[1]++;
            else {
                cnt[0]--;
                cnt[1]--;
            }
        }

        cnt[0] = 0;
        cnt[1] = 0;

        for (auto it : nums) {
            if (it == elem[0])
                cnt[0]++;
            else if (it == elem[1])
                cnt[1]++;
        }

        if (cnt[0] > n / 3 && cnt[1] > n / 3)
            return {elem[0], elem[1]};
        else if (cnt[0] > n / 3 && cnt[1] <= n / 3)
            return {elem[0]};
        else if (cnt[0] <= n / 3 && cnt[1] > n / 3)
            return {elem[1]};

        return {};
    }
};
```

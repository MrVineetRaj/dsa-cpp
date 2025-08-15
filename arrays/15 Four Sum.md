# Fou Sum

Given an integer array nums and an integer target. Return all quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

- a, b, c, d are all distinct valid indices of nums.

- nums[a] + nums[b] + nums[c] + nums[d] == target.

Notice that the solution set must not contain duplicate quadruplets. One element can be a part of multiple quadruplets. The output and the quadruplets can be returned in any order.

```cpp
class Solution {
   public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        set<vector<int>> s;
        int n = nums.size();

        sort(nums.begin(), nums.end());

        for (int i = 0; i < n - 3; i++) {
            for (int j = i + 1; j < n - 2; j++) {
                int l = j + 1;
                int r = n - 1;

                while (l < r) {
                    int sum = nums[i] + nums[l] + nums[r] + nums[j];

                    if (sum == target) {
                        vector<int> temp = {nums[i], nums[l], nums[r], nums[j]};
                        sort(temp.begin(), temp.end());

                        s.insert(temp);
                        l++;
                        r--;
                    } else if (sum < target) {
                        l++;
                    } else {
                        r--;
                    }
                }
            }
        }

        vector<vector<int>> ans;
        for (auto it : s) {
            ans.push_back(it);
        }

        return ans;
    }
};
```

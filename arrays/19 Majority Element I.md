# Majority Element I

Given an integer array nums of size n, return the majority element of the array.

The majority element of an array is an element that appears more than n/2 times in the array. The array is guaranteed to have a majority element.

```cpp
class Solution {
   public:
    int majorityElement(vector<int>& nums) {
        // brute : scanning complete array counting freq of each element
        // better : using hashmap
        // optimal : Moore's voting algorithm

        // Optimal Approach Solution

        int ans;
        int cnt = 0;
        int n = nums.size();

        for (int i = 0; i < n; i++) {
            if (cnt == 0) {
                ans = nums[i];
                cnt++;
            } else if (nums[i] == ans)
                cnt++;
            else
                cnt--;
        }

        cnt == 0;
        for (auto it : nums) {
            if (ans == it) {
                cnt++;
            }
        }

        if (cnt > n / 2) return ans;
        return -1;
    }
};
```

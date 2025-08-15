# Find missing number

Given an integer array of size n containing distinct values in the range from 0 to n (inclusive), return the only number missing from the array within this range.


```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int nsum = 0;
        int arraySum = 0;
        int n = nums.size();
        for(int i = 1; i <= n; i++){
            nsum+=i;
            arraySum+=nums[i-1];
        }

        return nsum - arraySum;
    }
};
```
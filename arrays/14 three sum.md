# Three sum

Given an integer array nums. Return all triplets such that:

- i != j, i != k, and j != k
- nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets. One element can be a part of multiple triplets. The output and the triplets can be returned in any order.

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        set<vector<int>> s;
        int n = nums.size();

        sort(nums.begin(),nums.end());

        for(int i = 0; i < n-2;i++){
            int l = i+1;
            int r = n-1;

            while( l < r){
                int sum = nums[i] + nums[l] + nums[r];

                if(sum  == 0){
                    vector<int> temp = {nums[i],nums[l],nums[r]};
                    sort(temp.begin(),temp.end());

                    s.insert(temp);
                    l++;
                    r--;
                }
                else if(sum < 0){
                    l++;
                }
                else{
                    r--;
                }
            }

        }

            vector<vector<int>> result;

            for(auto it: s){
                result.push_back(it);
            }

            return result;
    }
};
```

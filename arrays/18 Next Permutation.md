# Next Permutation

A permutation of an array of integers is an arrangement of its members into a sequence or linear order.

For example, for arr = [1,2,3], the following are all the permutations of arr:

[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1].

The next permutation of an array of integers is the next lexicographically greater permutation of its integers.

More formally, if all the permutations of the array are sorted in lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted order.

If such arrangement is not possible (i.e., the array is the last permutation), then rearrange it to the lowest possible order (i.e., sorted in ascending order).

You must rearrange the numbers in-place and use only constant extra memory.

```cpp
class Solution {
   public:
    void nextPermutation(vector<int>& nums) {
        int orderChangeAt = -1;
        int n = nums.size();
        for (int i = n - 1; i >= 1; i--) {
            if (nums[i] > nums[i - 1]) {
                orderChangeAt = i - 1;
                break;
            }
        }

        if (orderChangeAt == -1) {
            reverse(nums.begin(), nums.end());
            return;
        }

        // pivote where order is changed and then find just bigger then item
        // where orderchanged side

        for (int i = n - 1; i > orderChangeAt; i--) {
            if (nums[i] > nums[orderChangeAt]) {
                swap(nums[i], nums[orderChangeAt]);
                break;
            }
        }

        // sort the right part
        reverse(nums.begin() + orderChangeAt + 1, nums.end());
    }
};
```

for nums = [6, 7, 5, 9, 7, 6, 3, 2, 1]
orderChangeAt = 2
[6, 7, 6, 1, 2, 3, 5, 7, 9]

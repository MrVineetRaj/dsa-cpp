# Merge two sorted arrays without extra space

Given two integer arrays nums1 and nums2. Both arrays are sorted in non-decreasing order.

Merge both the arrays into a single array sorted in non-decreasing order.
- The final sorted array should be stored inside the array nums1 and it should be done in-place.
- nums1 has a length of m + n, where the first m elements denote the elements of nums1 and rest are 0s.
- nums2 has a length of n.

```cpp
class Solution {
   public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int left = m - 1;
        int right = 0;

        while (left >= 0 && right < n) {
            if (nums1[left] > nums2[right]) {
                swap(nums1[left--], nums2[right++]);
            } else {
                break;
            }
        }

        sort(nums1.begin(), nums1.begin() + m);
        sort(nums2.begin(), nums2.end());

        int i = 0;
        while (i < n) {
            nums1[m + i] = nums2[i];
            i++;
        }
    }
};
```

# Union of two sorted arrays

Given two sorted arrays nums1 and nums2, return an array that contains the union of these two arrays. The elements in the union must be in ascending order.

The union of two arrays is an array where all values are distinct and are present in either the first array, the second array, or both.

```cpp
class Solution {
   public:
    vector<int> unionArray(vector<int>& nums1, vector<int>& nums2) {
        int ptr1 = 0;
        int ptr2 = 0;

        int n1 = nums1.size();
        int n2 = nums2.size();

        vector<int> unionArray;
        while (ptr1 < n1 && ptr2 < n2) {

            while(ptr1 +1< n1 && nums1[ptr1] == nums1[ptr1 + 1]) ptr1++;
            while(ptr2 +1< n2 && nums2[ptr2] == nums2[ptr2 + 1]) ptr2++;

            if (nums1[ptr1] <= nums2[ptr2]) {
                if(nums1[ptr1] == nums2[ptr2]) ptr2++;
                unionArray.push_back(nums1[ptr1++]);
            }else {
                unionArray.push_back(nums2[ptr2++]);
            }
        }

        while (ptr1 < n1) {
            while(ptr1 +1< n1 && nums1[ptr1] == nums1[ptr1 + 1]) ptr1++;
            unionArray.push_back(nums1[ptr1++]);
        }
        while (ptr2 < n2) {
            while(ptr2 +1< n2 && nums2[ptr2] == nums2[ptr2 + 1]) ptr2++;
            unionArray.push_back(nums2[ptr2++]);
        }

        return unionArray;
    }
};
```

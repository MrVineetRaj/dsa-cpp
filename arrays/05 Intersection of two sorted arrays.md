# Intersection of two sorted arrays

Given two sorted arrays, nums1 and nums2, return an array containing the intersection of these two arrays. Each element in the result must appear as many times as it appears in both arrays.

The intersection of two arrays is an array where all values are present in both arrays.

```cpp
class Solution {
public:
    vector<int> intersectionArray(vector<int>& nums1, vector<int>& nums2) {
        vector<int> result;

        int n1 = nums1.size();
        int n2 = nums2.size();

        int ptr1 = 0;
        int ptr2 = 0;

        while(ptr1 <  n1 && ptr2 < n2){
            if(nums1[ptr1] < nums2[ptr2]) ptr1++;
            else if(nums1[ptr1] > nums2[ptr2]) ptr2++;

            else{
                result.push_back(nums1[ptr1++]);
                ptr2++;
            }
        }

        return result;
    }
};
```

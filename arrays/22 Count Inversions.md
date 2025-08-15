# Count Inversions

Given an integer array nums. Return the number of inversions in the array.

Two elements a[i] and a[j] form an inversion if a[i] > a[j] and i < j.

- It indicates how close an array is to being sorted.
- A sorted array has an inversion count of 0.
- An array sorted in descending order has maximum inversion.

```cpp
class Solution {
   private:
    void merge(vector<int> &nums, int s, int mid, int e, long long int &cnt) {
        vector<int> temp;
        int i = s, j = mid + 1;

        while (i <= mid && j <= e) {
            if (nums[i] <= nums[j]) {
                temp.push_back(nums[i++]);
            } else {
                temp.push_back(nums[j++]);
                cnt +=(mid - i + 1);  // All remaining elements in left part are inversions
            }
        }

        while (i <= mid) temp.push_back(nums[i++]);
        while (j <= e) temp.push_back(nums[j++]);

        for (int k = s; k <= e; ++k) nums[k] = temp[k - s];
    }

    void mergeSort(vector<int> &nums, int s, int e, long long int &cnt) {
        if (s >= e) return;
        int mid = s + (e - s) / 2;
        mergeSort(nums, s, mid, cnt);
        mergeSort(nums, mid + 1, e, cnt);
        merge(nums, s, mid, e, cnt);
    }

   public:
    long long int numberOfInversions(vector<int> nums) {
        // brute: Generate all pairs by scanning all other elements
        // for each selected elements and return count of such numbers

        // optimal : merge sort

        long long int cnt = 0;
        mergeSort(nums, 0, nums.size() - 1, cnt);
        return cnt;
    }
};
```

Tryout on [takeuforward/plus](https://takeuforward.org/plus/dsa/arrays/faqs-hard/count-inversions)

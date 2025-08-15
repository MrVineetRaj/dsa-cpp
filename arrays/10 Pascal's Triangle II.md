# Pascal's Triangle II

Given an integer r, return all the values in the rth row (1-indexed) in Pascal's Triangle in correct order.

In Pascal's triangle:

The first row has one element with a value of 1.
Each row has one more element in it than its previous row.
The value of each element is equal to the sum of the elements directly above it when arranged in a triangle format.

```cpp
class Solution {
   public:
    vector<int> pascalTriangleII(int row) {
        vector<int> ans;
        ans.push_back(1);

        /*
        for row 4
        simulating

        1    1*3/1    (1 * 3 * 2)/( 1 * 2)     (1 * 3 * 2 *1)/(1 * 2 * 3)
        1    3         3                          1
        */

        for (int i = 1; i < row; i++) {
            int temp = ans[i-1]*(row-i);
            temp/=i;
            ans.push_back(temp);
        }

        return ans;
    }
};
```

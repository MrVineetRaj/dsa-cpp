# Print the matrix in spiral manner

Given an M \* N matrix, print the elements in a clockwise spiral manner. Return an array with the elements in the order of their appearance when printed in a spiral manner.

```cpp
class Solution {
   public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int row = matrix.size();
        int col = matrix[0].size();
        int t = 0;
        int l = 0;
        int r = col - 1;
        int b = row - 1;

        vector<int> ans;
        int totalSize = row * col;
        while (l <= r && t <= b) {
            // if ( t <= b) {
                for (int i = l; i <= r; i++) {
                    ans.push_back(matrix[t][i]);
                }
                t++;
            // }
            // if ( r >= l) {
                for (int i = t; i <= b; i++) {
                    ans.push_back(matrix[i][r]);
                }
                r--;
            // }

            if ( t <= b) {
                for (int i = r; i >= l; i--) {
                    ans.push_back(matrix[b][i]);
                }
                b--;
            }

            if ( l <= r) {
                for (int i = b; i >= t; i--) {
                    ans.push_back(matrix[i][l]);
                }
                l++;
            }
        }

        return ans;
    }
};
```

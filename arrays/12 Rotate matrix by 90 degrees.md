# Rotate matrix by 90 degrees

Given an N \* N 2D integer matrix, rotate the matrix by 90 degrees clockwise.

The rotation must be done in place, meaning the input 2D matrix must be modified directly.

```cpp
class Solution {
public:
    void rotateMatrix(vector<vector<int>>& matrix) {
        int n = matrix.size();

        for(int i = 0; i < n; i++){
            for(int j = i ; j < n ; j++){
                swap(matrix[i][j],matrix[j][i]);
            }
        }

        for(int i = 0; i < n; i++){
            reverse(matrix[i].begin(),matrix[i].end());
        }
    }
};
```

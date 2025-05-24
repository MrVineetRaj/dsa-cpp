# Surrounded Regions

Given a matrix mat of size N x M where every element is either ‘O’ or ‘X’. Replace all ‘O’ with ‘X’ that is surrounded by ‘X’. An ‘O’ (or a set of ‘O’) is considered to be surrounded by ‘X’ if there are ‘X’ at locations just below, above, left, and right of it.

```cpp
class Solution {
   public:
    vector<vector<char>> fill(vector<vector<char>> mat) {
        int n = mat.size();
        int m = mat[0].size();

        vector<vector<bool>> notPossible(n, vector<bool>(m, false));

        vector<int> drow = {-1, 0, 1, 0};
        vector<int> dcol = {0, 1, 0, -1};

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if ((i == 0 || i == n - 1 || j == 0 || j == m - 1) &&
                    mat[i][j] == 'O' &&
                    !notPossible[i][j]
                    ) {
                    queue<pair<int, int>> q;
                    notPossible[i][j] = true;
                    q.push({i, j});

                    while (!q.empty()) {
                        int currRow = q.front().first;
                        int currCol = q.front().second;

                        q.pop();

                        for (int d = 0; d < 4; d++) {
                            int nrow = currRow + drow[d];
                            int ncol = currCol + dcol[d];

                            if (nrow >= 0 && nrow < n && ncol >= 0 &&
                                ncol < m && !notPossible[nrow][ncol] &&
                                mat[nrow][ncol] == 'O') {
                                q.push({nrow, ncol});
                                notPossible[nrow][ncol] = true;
                            }
                        }
                    }
                }
            }
        }

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (mat[i][j] == 'O' && !notPossible[i][j]) {
                    mat[i][j] = 'X';
                }
            }
        }

        return mat;
    }
};
```
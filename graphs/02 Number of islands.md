# Number of islands

Given a grid of size N x M (N is the number of rows and M is the number of columns in the grid) consisting of '0's (Water) and ‘1's(Land). Find the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically or diagonally i.e., in all 8 directions.

```cpp
typedef pair<int, int> P;

class Solution
{
public:
  int numIslands(vector<vector<char>> &grid)
  {
    int n = grid.size();
    int m = grid[0].size();
    vector<vector<bool>> vis(n, vector<bool>(m, false));

    int cnt = 0;

    int dRow[] = {-1, -1, -1, 0, 0, 1, 1, 1};
    int dCol[] = {-1, 0, 1, -1, 1, -1, 0, 1};

    for (int i = 0; i < n; i++)
    {
      for (int j = 0; j < m; j++)
      {
        if (grid[i][j] == '1' && !vis[i][j])
        {
          cnt++;
          queue<P> q;
          q.push({i, j});
          vis[i][j] = true;

          while (!q.empty())
          {
            auto [row, col] = q.front();
            q.pop();

            for (int d = 0; d < 8; d++)
            {
              int newRow = row + dRow[d];
              int newCol = col + dCol[d];

              if (newRow >= 0 && newRow < n && newCol >= 0 && newCol < m)
              {
                if (grid[newRow][newCol] == '1' && !vis[newRow][newCol])
                {
                  vis[newRow][newCol] = true;
                  q.push({newRow, newCol});
                }
              }
            }
          }
        }
      }
    }

    return cnt;
  }
};
```

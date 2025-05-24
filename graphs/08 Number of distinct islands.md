# Number of distinct islands

Given a boolean 2D matrix grid of size N x M. Find the number of distinct islands where a group of connected 1s (horizontally or vertically) forms an island. Two islands are considered to be distinct if and only if one island is equal to another (not rotated or reflected).

```cpp
class Solution
{
public:
    int countDistinctIslands(vector<vector<int>> &grid){
        int n = grid.size();
        int m = grid[0].size();
        vector<vector<bool>> vis(n,vector<bool>(m,false));
        set<vector<vector<int>>> s;

        vector<int> drow = {-1,0,1,0};
        vector<int> dcol = {0,1,0,-1};


        for(int i = 0; i < n ; i++){
            for(int j = 0; j< m;j++){
                if(grid[i][j] == 1 && !vis[i][j]){
                    queue<pair<int,int>> q;
                    q.push({i,j});
                    vis[i][j] = true;
                    
                    
                    vector<vector<int>> islandStructure;
                    islandStructure.push_back({i-i,j-j});
                    while(!q.empty()){
                        int currRow = q.front().first;
                        int currCol = q.front().second;
                        q.pop();

                        for(int d = 0 ; d < 4; d++){
                            int nrow = currRow + drow[d];
                            int ncol = currCol + dcol[d];
                            
                            if(nrow >= 0 &&
                                 nrow < n &&
                                 ncol >= 0 && 
                                 ncol < m && 
                                 !vis[nrow][ncol] && 
                                 grid[nrow][ncol] == 1
                                ){
                                    q.push({nrow,ncol});
                                    vis[nrow][ncol] = true;
                                    islandStructure.push_back({nrow-i,ncol-j});
                            }
                        }
                    }

                    sort(islandStructure.begin(),islandStructure.end());

                    s.insert(islandStructure);
                }
            }
        }
        return s.size();
    }
};
```
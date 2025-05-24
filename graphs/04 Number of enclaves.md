# Number of enclaves

Given an N x M binary matrix grid, where 0 represents a sea cell and 1 represents a land cell. A move consists of walking from one land cell to another adjacent (4-directionally) land cell or walking off the boundary of the grid. Find the number of land cells in the grid for which we cannot walk off the boundary of the grid in any number of moves.


```cpp
class Solution{
public:
    int numberOfEnclaves(vector<vector<int>> &grid) {
        int n = grid.size();
        int m = grid[0].size();
        vector<vector<bool>> vis(n,vector<bool>(m,false));

        vector<int> drow = {-1,0,1,0};
        vector<int> dcol = {0,1,0,-1};


        for(int i = 0; i < n ; i++){
            for(int j = 0; j< m;j++){
                if((i == 0 or i == n-1 or j == 0 or j == m-1 )and (grid[i][j] == 1)){
                    queue<pair<int,int>> q;
                    q.push({i,j});
                    vis[i][j] = true;


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
                            }
                        }
                    }
            
                }
            }
        }


        int cnt = 0;

        for(int i = 0; i < n ; i++){
            for(int j = 0; j< m;j++){
                if(!vis[i][j] && grid[i][j] == 1){
                    cnt++;
                }
            }
        }

        return cnt;

    }
};
```
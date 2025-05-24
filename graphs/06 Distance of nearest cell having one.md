# Distance of nearest cell having one

Given a binary grid of N x M. Find the distance of the nearest 1 in the grid for each cell.



The distance is calculated as |i1 - i2| + |j1 - j2|, where i1, j1 are the row number and column number of the current cell, and i2, j2 are the row number and column number of the nearest cell having value 1.


```cpp
class Solution{
public:
    vector<vector<int>> nearest(vector<vector<int>> grid){
        int m = grid[0].size();
        int n = grid.size();
        
        vector<vector<bool>> vis(n,vector<bool>(m,false));
        vector<vector<int>> ans(n,vector<int>(m,0));

        vector<int> drow = {-1,0,1,0};
        vector<int> dcol = {0,1,0,-1};

        queue<vector<int>> q;

        for(int i = 0; i < n; i++){
            for(int j = 0; j < m;j++){
                if(grid[i][j] == 1){
                    q.push({i,j,0});
                    vis[i][j] = true;
                    ans[i][j] = 0;
                }
            }
        }

        while(!q.empty()){
            int currRow = q.front()[0];
            int currCol = q.front()[1];
            int currDis = q.front()[2] + 1;
            q.pop();

            for(int d = 0 ; d < 4; d++){
                int nrow = currRow + drow[d];
                int ncol = currCol + dcol[d];
                if(nrow >= 0 &&
                        nrow < n &&
                        ncol >= 0 && 
                        ncol < m && 
                        !vis[nrow][ncol] && 
                        grid[nrow][ncol] == 0
                    ){
                        q.push({nrow,ncol,currDis});
                        vis[nrow][ncol] = true;
                        ans[nrow][ncol] = currDis;
                    }
                }
                        
            }
        

        return ans;
    }
};
```
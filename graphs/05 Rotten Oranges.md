# Rotten Oranges

Given an n x m grid, where each cell has the following values : 

- 2 - represents a rotten orange
- 1 - represents a Fresh orange
- 0 - represents an Empty Cell

Every minute, if a fresh orange is adjacent to a rotten orange in 4-direction ( upward, downwards, right, and left ) it becomes rotten. 


Return the minimum number of minutes required such that none of the cells has a Fresh Orange. If it's not possible, return -1.

```cpp
class Solution{
public:
    int orangesRotting(vector<vector<int>> &grid) {
        int m = grid[0].size();
        int n = grid.size();
        
        vector<vector<bool>> vis(n,vector<bool>(m,false));

        vector<int> drow = {-1,0,1,0};
        vector<int> dcol = {0,1,0,-1};
        
        
        int totalTimeTaken = 0;

        queue<vector<int>> q;

        for(int i = 0; i < n; i++){
            for(int j = 0; j < m;j++){
                if(grid[i][j] == 2){
                    q.push({i,j,0});
                    vis[i][j] = true;
                }
            }
        }
        while(!q.empty()){
            int currRow = q.front()[0];
            int currCol = q.front()[1];
            int currTime = q.front()[2];
            q.pop();

            totalTimeTaken = max(totalTimeTaken,currTime);

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
                        q.push({nrow,ncol,currTime+1});
                        vis[nrow][ncol] = true;
                        grid[nrow][ncol] = 2;
                    }
                }
                        
            }
        

        for(int i = 0; i < n; i++){
            for(int j = 0; j < m;j++){
                if(grid[i][j] == 1) return -1;
            }
        }

        return totalTimeTaken;
    }
};
```
# Number of provinces 

Given an undirected graph with V vertices. Two vertices u and v belong to a single province if there is a path from u to v or v to u. Find the number of provinces. The graph is given as an n x n matrix adj where adj[i][j] = 1 if the ith city and the jth city are directly connected, and adj[i][j] = 0 otherwise.



A province is a group of directly or indirectly connected cities and no other cities outside of the group.

```cpp
class Solution
{
public:
    int numProvinces(vector<vector<int>> adj) {
       
       int m = adj.size();

       int province = 0;
       vector<bool> visited(m,false);

       queue<int> q;

       for(int i = 0; i < m; i++){
            if(visited[i]){
                continue;
            }

            else{
                province++;
                q.push(i);
                visited[i] = true;

                while(!q.empty()){
                    int currNode = q.front();
                    q.pop();

                    for(int j = 0; j < m;j++){
                        if(adj[currNode][j] == 1 && !visited[j]){
                            q.push(j);
                            visited[j] = true;
                        }
                    }
                }
            }
       }

       return province;
    }
};
```
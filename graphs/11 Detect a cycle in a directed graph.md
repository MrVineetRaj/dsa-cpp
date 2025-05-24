# Detect a cycle in a directed graph

Given a directed graph with V vertices labeled from 0 to V-1. The graph is represented using an adjacency list where adj[i] lists all nodes connected to node. Determine if the graph contains any cycles.

```cpp
class Solution{
private:
    bool dfs(int node, vector<bool> &vis,vector<bool> &pathVis,vector<int> adj[]){
        vis[node] = true;
        pathVis[node] = true;

        for(auto it: adj[node]){
            // when node is not visited
            if(!vis[it]){
                if(dfs(it,vis,pathVis,adj)) return true;
            }else{
                // when node has Visited
                // is it visited on samepath
                if(pathVis[it]) return true;
            }
        }

        pathVis[node] = false;
        return false;
    }
public:
    bool isCyclic(int N, vector<int> adj[]) {
        vector<bool> vis(N,false);
        vector<bool> pathVis(N,false);

        for(int i = 0; i < N; i++){
            if(!vis[i]){
                if(dfs(i,vis,pathVis,adj)) return true;
            }
        }

        return false;
    }
};
```

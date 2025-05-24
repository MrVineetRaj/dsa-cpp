# Detect a cycle in an undirected graph

Given an undirected graph with V vertices labeled from 0 to V-1. The graph is represented using an adjacency list where adj[i] lists all nodes connected to node. Determine if the graph contains any cycles.

Note: The graph does not contain any self-edges (edges where a vertex is connected to itself).

```cpp
class Solution{
private:
bool detectCycleBFS(int src,vector<int> adj[],vector<int>  &vis){
    vis[src] = 1;
    queue<pair<int,int>> q;
    q.push({src,-1});
    while(!q.empty()){
        int node = q.front().first;
        int parent = q.front().second;

        q.pop();

        for(auto nnode:adj[node]){
            if(!vis[nnode]){
                vis[nnode] = 1;
                q.push({nnode,node});
            }else if(vis[nnode] && parent != nnode){
                return true;
            }
        }
    }
    return false;
}

bool detectCycleDFS(int src,int parent,vector<int> adj[],vector<int> &vis){

    vis[src] = 1;

    for(auto it:adj[src]){
        if(!vis[it]){
            if(detectCycleDFS(it,src,adj,vis)) return true;
        }else if(vis[it] && it != parent){
            return true;
        }
    }
    return false;
}
public:
    bool isCycle(int V, vector<int> adj[]) {
        vector<int> vis(V,0);

        for(int i  = 0; i < V;i++){
            if(!vis[i]){
                if(detectCycleDFS(i,-1,adj,vis)) return true;
            }
        }

        return false;
    }
};
```
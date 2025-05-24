# Bipartite graph

Given an undirected graph with V vertices labeled from 0 to V-1. The graph is represented using an adjacency list where adj[i] lists all nodes connected to node. Determine if the graph is bipartite or not.



A graph is bipartite if the nodes can be partitioned into two independent sets A and B such that every edge in the graph connects a node in set A and a node in set B.


```cpp
class Solution{
public:
    bool isBipartite(int V, vector<int> adj[])  {

        queue<int> q;
        vector<int> colorRecord(V,-1);

        for(int i  = 0; i < V;i++){
            if(colorRecord[i] == -1){
                q.push(i);
                colorRecord[i] = 0;

                while(!q.empty()){
                    int node = q.front();
                    q.pop();

                    for(auto it: adj[node]){
                        int expectedColor = colorRecord[node] == 1 ? 0 : 1;

                        if(colorRecord[it] == -1){
                            q.push(it);
                            colorRecord[it] = expectedColor;
                        }else if(expectedColor != colorRecord[it]){
                            return false;
                        }
                    }
                }
            }
        }

        return true;
    }
};
```
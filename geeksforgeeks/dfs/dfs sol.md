Below is the provided C++ code snippet with added comments:

```cpp
class Solution {
private:
    // Depth First Search (DFS) function to traverse the graph
    void dfs(int node, vector<int> adj[], int vis[], vector<int> &ls) {
        vis[node] = 1; // Mark the current node as visited
        ls.push_back(node); // Add the current node to the DFS traversal list
        
        // Traverse all neighbors of the current node
        for (auto it : adj[node]) {
            // If the neighbor is not visited, recursively call dfs
            if (!vis[it]) {
                dfs(it, adj, vis, ls);
            }
        }
    }

public:
    // Function to return a list containing the DFS traversal of the graph
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        int vis[V] = {0}; // Initialize an array to keep track of visited nodes
        int start = 0; // Start DFS traversal from node 0
        
        vector<int> ls; // Create a list to store the DFS traversal
        
        // Call DFS function to traverse the graph starting from node 0
        dfs(start, adj, vis, ls);
        
        return ls; // Return the DFS traversal list
    }
};
```

### Explanation:
- The `Solution` class defines a private function `dfs` and a public function `dfsOfGraph` to perform Depth First Search (DFS) traversal of a graph.
- The `dfs` function recursively traverses the graph starting from a given node and marks visited nodes.
- The `dfsOfGraph` function initializes an array to keep track of visited nodes, starts DFS traversal from node 0, and returns the DFS traversal list.

### Complexity Analysis:
- **Time Complexity:** O(V + E), where V is the number of vertices and E is the number of edges in the graph. The DFS traversal visits each vertex and each edge exactly once.
- **Space Complexity:** O(V), where V is the number of vertices. The space complexity is determined by the size of the visited array used to keep track of visited nodes.
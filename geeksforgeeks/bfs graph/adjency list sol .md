Here's the provided C++ code snippet with added comments:

```cpp
#include <bits/stdc++.h>
using namespace std;

// Class Solution to define the required function
class Solution {
public:
    // Function to return the adjacency list for each vertex.
    vector<vector<int>> printGraph(int V, vector<pair<int,int>> edges) {
        // Create a 2D vector to store the adjacency list
        vector<vector<int>> ans(V);
        
        // Iterate through the edges and add them to the adjacency list
        for (int i = 0; i < edges.size(); i++) {
            // Add the second vertex to the adjacency list of the first vertex
            ans[edges[i].first].push_back(edges[i].second);
            // Add the first vertex to the adjacency list of the second vertex
            ans[edges[i].second].push_back(edges[i].first);
        }
        
        return ans; // Return the adjacency list
    }
};

int main() {
    int tc;
    cin >> tc;
    while (tc--) {
        int V, E;
        cin >> V >> E;
        vector<pair<int,int>> edges;
        // Input the edges
        for (int i = 0; i < E; i++) {
            int u, v;
            cin >> u >> v;
            edges.push_back({u, v});
        }
        Solution obj; // Create an object of class Solution
        vector<vector<int>> adj = obj.printGraph(V, edges); // Get the adjacency list
        // Print the adjacency list
        for (int i = 0; i < V; i++) {
            sort(adj[i].begin(), adj[i].end()); // Sort the vertices in the adjacency list
            for (auto it : adj[i])
                cout << it << " ";
            cout << endl;
        }
    }
    return 0;
}
```

### Explanation:
- The `Solution` class defines a function `printGraph` to generate the adjacency list for each vertex in a graph.
- The main function reads the number of test cases (`tc`), and for each test case, it reads the number of vertices (`V`) and edges (`E`). It then reads the edges and stores them in the vector `edges`.
- Inside the loop, it creates an object `obj` of class `Solution` and calls the `printGraph` function to get the adjacency list for the current test case.
- It then sorts the vertices in each adjacency list and prints them.

### Complexity Analysis:
- **Time Complexity:** The time complexity of the `printGraph` function is O(E), where E is the number of edges, as it iterates through all the edges to build the adjacency list.
- **Space Complexity:** The space complexity is O(V + E), where V is the number of vertices and E is the number of edges, as the adjacency list requires space proportional to the number of vertices and edges in the graph.
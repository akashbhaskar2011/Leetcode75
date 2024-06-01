Here are two implementations for finding the left view of a binary tree. The left view of a binary tree contains all nodes that are first visible when the tree is viewed from the left side.

### BFS Approach (Level Order Traversal):

In this approach, we use a queue to perform level-order traversal and keep track of the first node of each level.

```cpp
vector<int> leftView(Node *root) {
    if (!root) return {};
    
    vector<int> ans;
    queue<Node*> q;
    q.push(root);
    
    while (!q.empty()) {
        int size = q.size();
        ans.push_back(q.front()->data);
        
        for (int i = 0; i < size; i++) {
            Node *temp = q.front();
            q.pop();
            if (temp->left) q.push(temp->left);
            if (temp->right) q.push(temp->right);
        }
    }
    
    return ans;
}
```

### DFS Approach (Recursive):

In this approach, we use Depth-First Search (DFS) and keep track of the maximum level visited so far. We use a helper function to recursively visit nodes, and update the result vector when visiting a new level for the first time.

```cpp
void helper(vector<int>& vec, Node *root, int level, int &maxlevel) {
    if (!root) return;
    
    if (maxlevel < level) {
        vec.push_back(root->data);
        maxlevel = level;
    }
    
    helper(vec, root->left, level + 1, maxlevel);
    helper(vec, root->right, level + 1, maxlevel);
}

vector<int> leftView(Node *root) {
    int maxlevel = 0;
    vector<int> ans;
    helper(ans, root, 1, maxlevel);
    return ans;
}
```

### Explanation:

1. **BFS Approach**:
   - **Queue Initialization**: Start with the root node in the queue.
   - **Level Traversal**: For each level, push the first node’s value to the result vector and then add its children to the queue.
   - **Result Update**: The first node in each level is added to the result vector.

2. **DFS Approach**:
   - **Recursive Traversal**: Traverse the tree using a helper function that keeps track of the current level and maximum level reached so far.
   - **Level Update**: If the current level is greater than the maximum level reached, add the node’s value to the result vector and update the maximum level.
   - **Left-First Traversal**: Ensure that left children are processed before right children to capture the left view.

Both approaches correctly capture the left view of the binary tree. The BFS approach uses an iterative method with a queue, while the DFS approach uses recursion. The choice between them depends on personal preference and specific use case requirements.
Certainly! Here are the same binary tree traversal methods implemented in C++ for both recursive and iterative approaches.

### Pre-order Traversal

#### Recursive
```cpp
struct TreeNode {
    int value;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : value(x), left(NULL), right(NULL) {}
};

void preorder_recursive(TreeNode* node) {
    if (node) {
        std::cout << node->value << " ";
        preorder_recursive(node->left);
        preorder_recursive(node->right);
    }
}
```

#### Iterative
```cpp
#include <stack>
#include <iostream>

void preorder_iterative(TreeNode* root) {
    if (!root) return;
    std::stack<TreeNode*> stack;
    stack.push(root);
    while (!stack.empty()) {
        TreeNode* node = stack.top();
        stack.pop();
        std::cout << node->value << " ";
        if (node->right) stack.push(node->right);
        if (node->left) stack.push(node->left);
    }
}
```

### In-order Traversal

#### Recursive
```cpp
void inorder_recursive(TreeNode* node) {
    if (node) {
        inorder_recursive(node->left);
        std::cout << node->value << " ";
        inorder_recursive(node->right);
    }
}
```

#### Iterative
```cpp
#include <stack>
#include <iostream>

void inorder_iterative(TreeNode* root) {
    std::stack<TreeNode*> stack;
    TreeNode* current = root;
    while (!stack.empty() || current) {
        while (current) {
            stack.push(current);
            current = current->left;
        }
        current = stack.top();
        stack.pop();
        std::cout << current->value << " ";
        current = current->right;
    }
}
```

### Post-order Traversal

#### Recursive
```cpp
void postorder_recursive(TreeNode* node) {
    if (node) {
        postorder_recursive(node->left);
        postorder_recursive(node->right);
        std::cout << node->value << " ";
    }
}
```

#### Iterative
```cpp
#include <stack>
#include <iostream>
#include <vector>

void postorder_iterative(TreeNode* root) {
    if (!root) return;
    std::stack<TreeNode*> stack1, stack2;
    stack1.push(root);
    while (!stack1.empty()) {
        TreeNode* node = stack1.top();
        stack1.pop();
        stack2.push(node);
        if (node->left) stack1.push(node->left);
        if (node->right) stack1.push(node->right);
    }
    while (!stack2.empty()) {
        TreeNode* node = stack2.top();
        stack2.pop();
        std::cout << node->value << " ";
    }
}
```

### Level-order Traversal (BFS)

#### Iterative
```cpp
#include <queue>
#include <iostream>

void levelorder_iterative(TreeNode* root) {
    if (!root) return;
    std::queue<TreeNode*> queue;
    queue.push(root);
    while (!queue.empty()) {
        TreeNode* node = queue.front();
        queue.pop();
        std::cout << node->value << " ";
        if (node->left) queue.push(node->left);
        if (node->right) queue.push(node->right);
    }
}
```

### Summary

- **Pre-order Traversal**:
  - **Recursive**: Visit current node, traverse left, then traverse right.
  - **Iterative**: Use a stack, visit node, push right, then left child to stack.

- **In-order Traversal**:
  - **Recursive**: Traverse left, visit current node, then traverse right.
  - **Iterative**: Use a stack, go left as far as possible, visit node, then go right.

- **Post-order Traversal**:
  - **Recursive**: Traverse left, traverse right, then visit current node.
  - **Iterative**: Use two stacks, push node to second stack after processing children.

- **Level-order Traversal**:
  - **Iterative**: Use a queue, visit nodes level by level.

These methods cover the primary ways to traverse a binary tree in C++ both recursively and iteratively.
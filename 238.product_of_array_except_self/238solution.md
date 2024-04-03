Certainly! Here's the commented version of your `Solution` class:

```cpp
#include <iostream>
#include <vector>

class Solution {
public:
    // # Intuition
    // The goal is to find the product of all elements in the array except the one at the current index.
    // We create a vector 'ans' to store the partial products. We iterate through the array from left to
    // right, calculating the product of elements to the left of each index and storing it in 'ans'. Then,
    // we iterate through the array from right to left, calculating the product of elements to the right
    // of each index and multiplying it with the corresponding value in 'ans'. The final 'ans' vector contains
    // the product of all elements except the one at each index.

    std::vector<int> productExceptSelf(std::vector<int>& nums) {
        int temp = 1;
        std::vector<int> ans;

        // Calculate the product of elements to the left of each index
        ans.push_back(1);
        temp *= nums[0];
        for (int i = 1; i < nums.size(); i++) {
            ans.push_back(temp);
            temp *= nums[i];
        }

        temp = 1;

        // Calculate the product of elements to the right of each index and multiply with the corresponding 'ans' value
        temp = temp * nums[nums.size() - 1];
        for (int i = nums.size() - 2; i >= 0; i--) {
            ans[i] *= temp;
            temp = temp * nums[i];
        }

        return ans;
    }
};
```

This version includes comments explaining the intuition and approach of the `Solution` class.

Here's the modified code without recursion:

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */

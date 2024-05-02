Here's the provided C++ code snippet with added comments:

```cpp
class Solution {
public:
    // Function to find the minimum path sum in a grid
    int minPathSum(vector<vector<int>>& grid) {
        int m = grid.size(); // Get the number of rows in the grid
        int n = grid[0].size(); // Get the number of columns in the grid

        // Iterate through each cell in the grid
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                int left = (j != 0) ? grid[i][j - 1] : INT_MAX; // Get the value from the cell to the left
                int above = (i != 0) ? grid[i - 1][j] : INT_MAX; // Get the value from the cell above

                // If both left and above are unreachable, continue to the next iteration
                if (left == INT_MAX && above == INT_MAX) 
                    continue;

                // If left is reachable and smaller than above, update the current cell with the sum of left and current cell
                if (left != INT_MAX && (above == INT_MAX || left < above))
                    grid[i][j] += left;

                // If above is reachable and smaller than or equal to left, update the current cell with the sum of above and current cell
                else if (above != INT_MAX && (left == INT_MAX || above <= left))
                    grid[i][j] += above;
            }
        }
        // Return the minimum path sum which is stored in the bottom-right cell of the grid
        return grid[m - 1][n - 1];
    }
};
```

### Explanation:
- This function aims to find the minimum path sum in a grid where each cell contains a non-negative integer.
- It uses dynamic programming to calculate the minimum path sum efficiently.
- The function iterates through each cell in the grid and calculates the minimum path sum considering the values from the cells to the left and above.
- It updates each cell with the minimum path sum from the top-left corner to that cell.
- Finally, it returns the value stored in the bottom-right cell of the grid, which represents the minimum path sum.

### Complexity Analysis:
- **Time complexity:** O(m * n), where m is the number of rows and n is the number of columns in the grid. The function iterates through each cell in the grid once.
- **Space complexity:** O(1), as the function modifies the input grid in place without using any additional space except for a few variables.
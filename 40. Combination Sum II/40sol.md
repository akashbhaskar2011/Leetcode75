Here's the provided C++ code snippet with added comments:

```cpp
class Solution {
private:
    // Helper function to find combinations that sum up to the target
    void helper(int start, vector<int>& cand, int target, vector<vector<int>>& ans, vector<int>& combi) {
        // Base case: if the target is reached, add the combination to the answer
        if (target == 0) {
            ans.push_back(combi);
            return;
        }

        // Iterate over the candidates starting from 'start'
        for (int i = start; i < cand.size() && target >= cand[i]; i++) {
            // Skip duplicate candidates to avoid duplicate combinations
            if (i > start && cand[i] == cand[i - 1])
                continue;

            combi.push_back(cand[i]); // Include the current candidate in the combination
            helper(i + 1, cand, target - cand[i], ans, combi); // Recursively explore further with updated target
            combi.pop_back(); // Backtrack: remove the last candidate from the combination
        }
    }

public:
    // Function to find all unique combinations that sum up to the target
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<vector<int>> ans; // Vector to store all combinations
        vector<int> combi; // Vector to store a single combination

        // Sort the candidates to handle duplicates
        sort(candidates.begin(), candidates.end());

        // Call the helper function to find combinations
        helper(0, candidates, target, ans, combi);

        return ans; // Return the list of combinations
    }
};
```

### Intuition and Approach:
This function aims to find all unique combinations of numbers from the given candidates that sum up to the target. It utilizes backtracking to explore all possible combinations while avoiding duplicates.

### Steps:
1. Define a helper function `helper` to recursively find combinations:
   - Base case: If the target is reached (`target == 0`), add the current combination to the answer.
   - Iterate over the candidates starting from `start`:
     - Skip duplicate candidates to avoid duplicate combinations.
     - Include the current candidate in the combination.
     - Recursively call the function with the updated target and starting index.
     - Backtrack by removing the last candidate from the combination.
2. Initialize an empty vector `ans` to store all combinations.
3. Initialize an empty vector `combi` to store a single combination.
4. Sort the candidates to handle duplicates.
5. Call the helper function with the candidates, target, an empty combination, and the starting index 0.
6. Return the list of combinations.

### Complexity Analysis:
- **Time complexity:** The time complexity depends on the number of combinations generated. In the worst case, it is exponential, as each candidate has two choices (to include or exclude) for each recursive call.
- **Space complexity:** The space complexity depends on the number of recursive calls and the size of the combinations stored in the answer. It is also exponential in the worst case.
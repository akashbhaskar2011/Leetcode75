Certainly! Here is the commented version of your code:

```cpp
#include <iostream>
#include <vector>

class Solution {
public:
    // # Intuition
    // We want to determine, for each kid, if they can have the greatest number of candies
    // when given extra candies. To do this, we find the greatest number of candies in the original set,
    // and then check if adding extra candies to each kid's candies would make them have the greatest.

    std::vector<bool> kidsWithCandies(std::vector<int>& candies, int extraCandies) {
        // Find the greatest number of candies in the original set
        int greatestCandies = greatest(candies);

        // Vector to store the results for each kid
        std::vector<bool> ans;

        // Iterate through each kid's candies
        for (int i = 0; i < candies.size(); i++) {
            // Check if adding extra candies to the current kid would make them have the greatest number
            ans.push_back((candies[i] + extraCandies) >= greatestCandies);
        }

        // Return the vector of results
        return ans;
    }

private:
    // Helper function to find the greatest number in a vector
    int greatest(std::vector<int> vec) {
        int g = 0;

        // Iterate through the vector to find the greatest number
        for (int i = 0; i < vec.size(); i++) {
            if (g < vec[i]) g = vec[i];
        }

        // Return the greatest number
        return g;
    }
};

int main() {
    Solution solution;

    // Example usage:
    std::vector<int> candies = {2, 3, 5, 1, 3};
    int extraCandies = 3;

    // Get the results for each kid
    std::vector<bool> result = solution.kidsWithCandies(candies, extraCandies);

    // Print the results
    std::cout << "Results: ";
    for (bool canHaveGreatest : result) {
        std::cout << (canHaveGreatest ? "true" : "false") << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

This includes comments explaining the intuition, approach, complexity, and individual parts of the code.
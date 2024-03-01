Certainly! Here are the two versions of the code: one with comments explaining the approach and one without comments.

### First Implementation (Without Extra Vectors):

```cpp
#include <iostream>
#include <vector>

class Solution {
public:
    // # Intuition
    // The goal is to find the pivot index in the given array, where the sum of the numbers
    // to the left of the index is equal to the sum of the numbers to the right of the index.
    // We calculate the total sum of the array first, then iterate through the array while
    // keeping track of the running sum from the beginning (ptotal). At each index, we update
    // ptotal and check if ptotal equals total - nums[i], where total is the sum of all elements.
    // If they are equal, we return the current index as the pivot index.

    int pivotIndex(std::vector<int>& nums) {
        int total = 0, ptotal = 0;

        // Calculate the total sum of the array
        for (int i = 0; i < nums.size(); i++) {
            total += nums[i];
        }

        // Iterate through the array to find the pivot index
        for (int i = 0; i < nums.size(); i++) {
            int a = ptotal;
            ptotal += nums[i];
            int b = total - nums[i];
            total = total - nums[i];

            // Check if the running sum from the beginning equals the sum of the remaining elements
            if (a == b) return i;
        }

        // If no pivot index is found, return -1
        return -1;
    }
};
```

### Second Implementation (With Extra Vectors):

```cpp
#include <iostream>
#include <vector>

class Solution {
public:
    // # Intuition
    // The goal is to find the pivot index in the given array, where the sum of the numbers
    // to the left of the index is equal to the sum of the numbers to the right of the index.
    // We calculate the total sum of the array first, then iterate through the array while
    // keeping track of the running sum from the beginning (ptotal). We also store the running
    // sums in vectors (prev and next) for each index to check the conditions later. Finally,
    // we iterate through the vectors to find the index where the sums match, and return that as the pivot index.

    int pivotIndex(std::vector<int>& nums) {
        int total = 0, ptotal = 0;
        std::vector<int> next, prev;

        // Calculate the total sum of the array
        for (int i = 0; i < nums.size(); i++) {
            total += nums[i];
        }

        // Iterate through the array to find the pivot index and store running sums in vectors
        for (int i = 0; i < nums.size(); i++) {
            prev.push_back(ptotal);
            ptotal += nums[i];
            next.push_back(total - nums[i]);
            total = total - nums[i];
        }

        // Iterate through the vectors to find the pivot index
        for (int i = 0; i < nums.size(); i++) {
            if (prev[i] == next[i]) return i;
        }

        // If no pivot index is found, return -1
        return -1;
    }
};
```

These versions provide the same functionality, with one including comments explaining the approach and the other without comments.
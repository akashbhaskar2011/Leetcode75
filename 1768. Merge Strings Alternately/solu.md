

```cpp
#include <iostream>
using namespace std;

class Solution {
public:
    // # Intuition
    // We want to merge two strings alternately, taking one character from each string
    // until one of the strings is exhausted, then append the remaining characters from the other string.

    string mergeAlternately(string word1, string word2) {
        // Resultant string to store the alternately merged characters
        string newString;

        // Pointers to keep track of the current position in each string
        int word1Pos = 0;
        int word2Pos = 0;

        // # Approach
        // Use a loop to iterate through the combined length of both strings
        for (int i = 0; i < word1.size() + word2.size(); i++) {
            // Check if there are still characters left in word1
            if (word1Pos < word1.size()) {
                // Append the character from word1 to the newString and increment the pointer
                newString += word1[word1Pos++];
            }

            // Check if there are still characters left in word2
            if (word2Pos < word2.size()) {
                // Append the character from word2 to the newString and increment the pointer
                newString += word2[word2Pos++];
            }
        }

        // The loop ensures we've alternately merged characters.
        // Remaining characters (if any) from either string are already appended.

        // Return the final alternately merged string
        return newString;
    }
};

int main() {
    Solution solution;

    // Example usage
    std::string word1 = "abc";
    std::string word2 = "12";

    // Get the alternately merged result
    std::string mergedResult = solution.mergeAlternately(word1, word2);

    // Print the result
    std::cout << "Merged Result: " << mergedResult << std::endl;

    return 0;
}

# Complexity
- Time complexity: O(n), where n is the combined length of the two input strings.
- Space complexity: O(n), as we are using an additional string to store the merged result.
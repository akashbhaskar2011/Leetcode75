Here's the `Solution` class with a function to find the longest palindromic substring in a given string `s`. This solution uses a brute-force approach to check all possible substrings, which can be optimized, but I'll present it as per the provided code structure.

```cpp
class Solution {
public:
    bool isPalindrome(string temp) {
        int i = 0; 
        int len = temp.length() - 1;
        while (i <= len) {
            if (temp[i++] != temp[len--]) 
                return false;
        }
        return true;
    }

    string longestPalindrome(string s) {
        string temp = "", ans = "";
        int len = s.length();
        for (int i = 0; i < len; i++) {
            for (int j = i; j < len; j++) {
                temp = s.substr(i, j - i + 1);
                if (isPalindrome(temp) && ans.length() < temp.length()) {
                    ans = temp;
                }
            }
        }
        return ans;
    }
};
```

### Explanation

1. **isPalindrome Function:**
   - This function takes a string `temp` and checks if it is a palindrome.
   - It uses two pointers, `i` starting from the beginning and `len` starting from the end of the string.
   - It compares characters from both ends moving towards the center. If any characters don't match, it returns `false`. If all characters match, it returns `true`.

2. **longestPalindrome Function:**
   - This function takes a string `s` and returns the longest palindromic substring.
   - It initializes two empty strings, `temp` for the current substring and `ans` for the longest palindromic substring found.
   - It uses two nested loops to generate all possible substrings of `s`. The outer loop starts the substring at index `i`, and the inner loop ends the substring at index `j`.
   - For each substring `temp`, it checks if it is a palindrome and if its length is greater than the current longest palindrome stored in `ans`. If both conditions are met, it updates `ans` with `temp`.
   - Finally, it returns `ans`.

### Complexity

- **Time Complexity:** O(n^3)
  - The outer loop runs `n` times.
  - The inner loop runs `n` times for each iteration of the outer loop.
  - The `isPalindrome` function runs O(n) for each substring.
  - Hence, the overall time complexity is O(n^3).
  
- **Space Complexity:** O(1)
  - The space used by the `isPalindrome` function is constant, and only a few extra variables are used.

### Optimized Approach

This brute-force method has a high time complexity. A more efficient approach would be to use dynamic programming or expand around the center method, which can reduce the time complexity to O(n^2). Here’s a brief look at how the expand around the center method works:

- Consider each character and the pair of characters as the center of a potential palindrome.
- Expand outwards as long as the substring remains a palindrome.
- Track the longest palindrome found during this process.
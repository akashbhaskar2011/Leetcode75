This `Solution` class implements the `longestPalindrome` function, which finds the longest palindromic substring in a given string `s` using the expand around the center approach. Let's break down the code:

```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        int len = s.length();
        string ans = "", temp = "";
        for (int i = 0; i < len; i++) {
            int l = i, r = i;
            // Expand around center with single character as center
            while (l >= 0 && r < len && s[l] == s[r]) {
                l--;
                r++;
            }
            temp = s.substr(l + 1, r - l - 1);
            if (temp.length() > ans.length()) {
                ans = temp;
            }
            // Expand around center with two characters as center
            l = i, r = i + 1;
            while (l >= 0 && r < len && s[l] == s[r]) {
                l--;
                r++;
            }
            temp = s.substr(l + 1, r - l - 1);
            if (temp.length() > ans.length()) {
                ans = temp;
            }
        }
        return ans;
    }
};
```

### Explanation:

- The `longestPalindrome` function takes a string `s` and returns the longest palindromic substring found in `s`.
- It initializes two empty strings, `ans` for storing the longest palindromic substring and `temp` for storing the current palindromic substring being checked.
- It iterates through each character in the string `s`.
- For each character, it performs the following steps:
  - It initializes two pointers `l` and `r` to the current index `i`.
  - It expands `l` towards the left and `r` towards the right as long as the characters at positions `l` and `r` are the same, and `l` and `r` are within the bounds of the string.
  - After the expansion, it calculates the length of the palindromic substring found and updates `temp` accordingly using `substr`.
  - If the length of `temp` is greater than the length of `ans`, it updates `ans` with `temp`.
  - It repeats the above steps for the case where the center of the palindrome consists of two characters.
- Finally, it returns the longest palindromic substring found stored in `ans`.

### Complexity Analysis:

- **Time Complexity:** O(n^2)
  - The algorithm iterates through each character in the string, and for each character, it performs constant-time expansions around the center.
  - Therefore, the overall time complexity is O(n^2), where n is the length of the input string.
  
- **Space Complexity:** O(1)
  - The space complexity is constant as only a few extra variables are used regardless of the size of the input string.
Your implementation of the `strStr` function is correct and efficient for finding the first occurrence of the `needle` string within the `haystack` string. Here’s a slightly cleaned-up version without the debug `cout` statements, which is more suitable for production:

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int nlen = needle.length();
        int hlen = haystack.length();
        
        for (int i = 0; i <= hlen - nlen; i++) {
            if (haystack.substr(i, nlen) == needle) {
                return i;
            }
        }
        return -1;
    }
};
```

### Explanation:

1. **Length Calculation**:
   - `nlen` is the length of the `needle` string.
   - `hlen` is the length of the `haystack` string.

2. **Loop Through `haystack`**:
   - The loop runs from `i = 0` to `i <= hlen - nlen`. This ensures we only check valid starting positions in the `haystack` where the `needle` can fit.
   - `haystack.substr(i, nlen)` creates a substring of `haystack` starting at index `i` with a length of `nlen`.

3. **Check Substring**:
   - If the substring equals the `needle`, return the current index `i`.

4. **Return -1 If Not Found**:
   - If the loop completes without finding the `needle`, return `-1`.

### Potential Optimizations:

While your approach is straightforward and works well for smaller strings, for very large strings, it could be less efficient due to the repeated substring operations. An alternative, more efficient algorithm would be the Knuth-Morris-Pratt (KMP) algorithm, which preprocesses the `needle` to allow faster searching within the `haystack`. However, for many use cases, the current implementation will be sufficiently efficient.

Here’s a quick outline of the KMP approach:

```cpp
class Solution {
public:
    vector<int> computeLPSArray(string needle) {
        int nlen = needle.length();
        vector<int> lps(nlen, 0);
        int length = 0; // length of the previous longest prefix suffix
        int i = 1;
        while (i < nlen) {
            if (needle[i] == needle[length]) {
                length++;
                lps[i] = length;
                i++;
            } else {
                if (length != 0) {
                    length = lps[length - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }
        return lps;
    }

    int strStr(string haystack, string needle) {
        if (needle.empty()) return 0;
        int hlen = haystack.length();
        int nlen = needle.length();
        
        vector<int> lps = computeLPSArray(needle);
        
        int i = 0; // index for haystack
        int j = 0; // index for needle
        while (i < hlen) {
            if (needle[j] == haystack[i]) {
                i++;
                j++;
            }
            
            if (j == nlen) {
                return i - j;
            } else if (i < hlen && needle[j] != haystack[i]) {
                if (j != 0) {
                    j = lps[j - 1];
                } else {
                    i++;
                }
            }
        }
        return -1;
    }
};
```

This KMP version preprocesses the `needle` to create an array of the longest prefix suffix (LPS), which is then used to skip unnecessary comparisons while searching through the `haystack`.
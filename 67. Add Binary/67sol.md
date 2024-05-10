This C++ function, `addBinary`, takes two binary strings `a` and `b` as input and returns their sum as a binary string.

Here's the provided code with added comments for clarity:

```cpp
class Solution {
public:
    string addBinary(string a, string b) {
        int carry = 0; // Initialize carry to 0
        string ans = ""; // Initialize the answer string
        
        int i = a.length() - 1; // Initialize index i to the last character of string a
        int j = b.length() - 1; // Initialize index j to the last character of string b
        
        // Iterate from the end of the strings to the beginning or until carry is non-zero
        while (i >= 0 || j >= 0 || carry) {
            int num_a = (i >= 0) ? a[i] - '0' : 0; // Convert the character at index i to an integer
            int num_b = (j >= 0) ? b[j] - '0' : 0; // Convert the character at index j to an integer
            int sum = num_a + num_b + carry; // Calculate the sum of current digits and the carry
            
            ans = to_string(sum % 2) + ans; // Append the remainder of sum % 2 to the answer string
            carry = sum / 2; // Update carry to the quotient of sum / 2
            
            i--; // Move to the next character in string a
            j--; // Move to the next character in string b
        }
        
        return ans; // Return the final binary sum as a string
    }
};
```

### Explanation:
- The function starts by initializing `carry` to 0 and an empty string `ans` to store the binary sum.
- It then iterates through both input strings from right to left (least significant bit to most significant bit) using indices `i` and `j`.
- During each iteration, it calculates the sum of the current digits from `a`, `b`, and the carry.
- The remainder of the sum modulo 2 is appended to the beginning of the answer string `ans`, and the quotient of the sum divided by 2 becomes the new carry.
- Finally, the function returns the binary sum as a string.

### Complexity Analysis:
- **Time Complexity:** O(max(N, M)), where N and M are the lengths of the input strings `a` and `b`, respectively. The function iterates through both input strings once.
- **Space Complexity:** O(max(N, M)), where N and M are the lengths of the input strings `a` and `b`, respectively. The space complexity is determined by the size of the answer string, which can be at most max(N, M) + 1 characters long.
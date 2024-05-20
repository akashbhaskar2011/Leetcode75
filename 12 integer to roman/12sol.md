Your code for converting an integer to a Roman numeral is efficient and correctly implemented. The solution involves mapping the most significant Roman numeral values to their corresponding symbols and iterating through the integer to build the Roman numeral string.

Here's a slightly optimized and clean version of your code:

```cpp
class Solution {
public:
    string intToRoman(int num) {
        string ans = "";
        string key[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int value[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        
        for (int i = 0; i < 13; i++) {
            while (num >= value[i]) {
                ans += key[i];
                num -= value[i];
            }
        }
        return ans;
    }
};
```

### Explanation:
- **String Arrays for Roman Symbols and Their Values**: Two arrays are used to store the Roman numeral symbols (`key`) and their corresponding integer values (`value`).
- **Loop Through the Values**: The loop iterates through each value in the `value` array.
  - **While Loop for Subtraction**: Within each iteration of the outer loop, a while loop keeps subtracting the current `value[i]` from `num` until `num` is less than `value[i]`. For each subtraction, the corresponding Roman numeral symbol is appended to the result string `ans`.
- **Return the Result**: After the loop completes, the final Roman numeral string is returned.

This approach ensures that the largest possible Roman numeral symbols are used first, making the conversion process efficient and straightforward.
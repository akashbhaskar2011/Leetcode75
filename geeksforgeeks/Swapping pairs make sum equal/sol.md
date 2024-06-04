Here's a detailed explanation with comments, intuition, and complexity analysis for the given code:

```cpp
class Solution {
  public:
    int findSwapValues(int a[], int n, int b[], int m) {
        // Calculate the sum of elements in array a and array b
        int suma = 0, sumb = 0;
        for (int i = 0; i < n; i++) {
            suma += a[i];
        }
        for (int i = 0; i < m; i++) {
            sumb += b[i];
        }

        // Sort both arrays to use two-pointer technique efficiently
        sort(a, a + n);
        sort(b, b + m);

        // If the difference between sums is odd, return -1 as no solution is possible
        if ((suma - sumb) % 2 != 0) return -1;

        // Calculate the difference divided by 2
        int diff = (suma - sumb) / 2;
        int i = 0, j = 0;

        // Use two-pointer technique to find the correct elements to swap
        while (i < n && j < m) {
            if (a[i] - diff == b[j]) {
                // If the required swap pair is found, return 1
                return 1;
            } else if (a[i] - diff < b[j]) {
                // If the current element in a is too small, move to the next element in a
                i++;
            } else {
                // If the current element in b is too small, move to the next element in b
                j++;
            }
        }

        // If no swap pair is found, return -1
        return -1;
    }
};
```

### Intuition:
1. **Sum Calculation**: First, calculate the sums of both arrays, `suma` for array `a` and `sumb` for array `b`.
2. **Sorting**: Sort both arrays to facilitate efficient searching using the two-pointer technique.
3. **Difference Check**: Check if the difference between the sums is even. If it's odd, a swap is impossible, so return `-1`.
4. **Two-Pointer Technique**: Use two pointers to find a pair `(a[i], b[j])` such that swapping them equalizes the sums of the two arrays. This is achieved by checking if `a[i] - b[j] == diff`, where `diff` is `(suma - sumb) / 2`.

### Complexity Analysis:
- **Time Complexity**:
  - Calculating the sum of elements in both arrays takes `O(n + m)`.
  - Sorting both arrays takes `O(n log n + m log m)`.
  - The two-pointer traversal takes `O(n + m)` in the worst case.
  - Overall time complexity: `O(n log n + m log m)`.

- **Space Complexity**:
  - The algorithm uses a constant amount of extra space, `O(1)`, as it only requires a few additional variables for pointers and sums.

This approach efficiently finds the solution using sorting and the two-pointer technique, ensuring that it runs in a reasonable time even for larger inputs.
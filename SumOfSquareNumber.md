# Sum of square Number:

> Question link:
> https://leetcode.com/problems/sum-of-square-numbers/description/?envType=daily-question&envId=2024-06-17

### Approach:

1. **Base Case Check**: 
   - If `c` is negative, return `false` because a negative number cannot be expressed as a sum of two squares.

2. **Two Pointers Initialization**: 
   - Initialize `left` to 0 and `right` to the integer square root of `c` (`sqrt(c)`). These pointers will help us explore possible pairs `(left, right)`.

3. **Two Pointers Technique**:
   - Use a while loop that continues as long as `left` is less than or equal to `right`.
   - Calculate the sum of squares `left * left + right * right`.
   - If the sum equals `c`, return `true` because we found a pair `(left, right)` that sums to `c`.
   - If the sum is less than `c`, increment `left` to try a larger value.
   - If the sum is greater than `c`, decrement `right` to try a smaller value.

4. **Termination**:
   - If the while loop finishes without finding a sum equal to `c`, return `false`.


### Code:

```C++

    bool judgeSquareSum(int c) {
        // Check for the base cases
        if (c < 0) {
            return false;
        }

        // Use two pointers approach
        long long left = 0;
        long long right = static_cast<long long>(sqrt(c));

        while (left <= right) {
            long long sum = left * left + right * right;

            if (sum == c) {
                return true;
            } else if (sum < c) {
                left++;
            } else {
                right--;
            }
        }

        return false;
    }

```

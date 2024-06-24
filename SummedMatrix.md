# Summed Matrix:

>Question link:
>https://www.geeksforgeeks.org/problems/summed-matrix5834/1


### Approach:

3. **Key Insight**:
   - For a given \( i \), the values in the \( i \)-th row range from \( i+1 \) to \( i+n \), where \( n \) is the size of the matrix.
   - Thus, \( M(i, j) \) for \( j \) ranging from \( 1 \) to \( n \) gives us values \( i+1, i+2, \ldots, i+n \).

4. **Counting Occurrences of \( q \)**:
   - To count how many times \( q \) appears in the matrix:
     - We need to determine which rows \( i \) satisfy \( M(i, j) = q \).
     - This translates to finding all \( i \) such that \( i + j = q \) for some \( j \) within \( 1 \) to \( n \).

5. **Mathematical Formulation**:
   - For a given \( q \), \( i \) must satisfy \( i = q - j \) where \( 1 \leq j \leq n \).
   - Therefore, \( i \) must be in the range \( max(1, q-n) \) to \( min(n, q-1) \).

6. **Calculating the Number of Occurrences**:
   - If \( q \) is less than \( 1 \) or greater than \( 2n \), it's impossible for \( q \) to be a value in the matrix because the minimum and maximum possible values of \( M(i, j) \) are \( 2 \) and \( 2n \).
   - Otherwise, calculate the range of \( i \) values where \( M(i, j) = q \):
     - int min_i = max(1, q - n) \)
     - int max_i =  min(n, q - 1) \)
   - The number of occurrences of \( q \) is `max(0, max_i - min_i + 1)`.

### Code:
```cpp

int countCellsWithValue(int n, int q) {
    // Edge case where q is out of range of possible values in the matrix
    if (q < 2 || q > 2 * n) {
        return 0;
    }

    // Calculate the range of valid i values
    int min_i = max(1, q - n);
    int max_i = min(n, q - 1);

    // Calculate the number of occurrences of q
    int count = max(0, max_i - min_i + 1);

    return count;
}

```

**Time Complexity:** `O(1)`, as the time complexity is constant.

**Space Complexity:** `O(1)`, as no extra space is used.


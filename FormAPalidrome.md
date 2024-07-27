# Form a palidrome:

> Question link:
> https://www.geeksforgeeks.org/problems/form-a-palindrome1455/1

### Approach:

1. **Define the DP Table:**
   - Create a 2D table `dp` where `dp[i][j]` will store the length of the longest palindromic subsequence in the substring `str[i...j]`.

2. **Initialize the DP Table:**
   - For substrings of length 1 (i.e., single characters), the LPS length is 1. Initialize `dp[i][i] = 1` for all `i`.

3. **Fill the DP Table:**
   - **For Substrings of Length 2:**
     - If `str[i] == str[j]`, then `dp[i][j] = 2` because the substring is already a palindrome of length 2.
     - If `str[i] != str[j]`, then `dp[i][j] = 1` (only the longer of the two substrings `str[i+1...j]` and `str[i...j-1]`).
   - **For Longer Substrings:**
     - Iterate over all possible substring lengths from 3 to `n`.
     - For each substring `str[i...j]`:
       - If `str[i] == str[j]`, set `dp[i][j] = dp[i + 1][j - 1] + 2` because the characters at the ends match and contribute to the LPS.
       - If `str[i] != str[j]`, set `dp[i][j] = max(dp[i + 1][j], dp[i][j - 1])` because you take the maximum LPS length by either including or excluding the current characters at the ends.

4. **Calculate the Minimum Insertions:**
   - Once the DP table is filled, the length of the longest palindromic subsequence for the entire string is `dp[0][n - 1]`.
   - The minimum number of insertions required to make the string a palindrome is computed as:
     \[ \text{Minimum Insertions} = \text{Length of String} - \text{Length of LPS} \]


### Code:

```C++
    int minInsertionsToPalindrome(string& str) {
    int n = str.length();
    // Create a 2D table to store results of subproblems
    vector<vector<int>> dp(n, vector<int>(n, 0));

    // Fill the table
    for (int length = 2; length <= n; ++length) {
        for (int i = 0; i < n - length + 1; ++i) {
            int j = i + length - 1;
            if (str[i] == str[j]) {
                dp[i][j] = dp[i + 1][j - 1];
            } else {
                dp[i][j] = min(dp[i + 1][j], dp[i][j - 1]) + 1;
            }
        }
    }

    // The answer is in dp[0][n-1]
    return dp[0][n - 1];
}
```

**Time Complexity** `O(N^2)` , where N is the length of the string.

**Space Complexity** `O(N^2)`, where N is the length of the string.



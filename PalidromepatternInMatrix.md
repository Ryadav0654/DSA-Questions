# The Palidrome Pattern in Matrix:

> Question link:
> https://www.geeksforgeeks.org/problems/the-palindrome-pattern3900/1


### Code:

```C++
private:
    // Check if the given vector is a palindrome or not
    bool checkPalindrome(vector<int> v) {
        // copy the vector
        vector<int> temp = v;
        // reverse the vector
        reverse(v.begin(), v.end());

        // if both are equal then return true
        return v == temp;
    }

public:
    string pattern(vector<vector<int>> &arr) {
        // find the length
        int len = arr.size();

        // Check rows for palindrome
        for (int i = 0; i < len; i++) {
            // create a temporary vector
            vector<int> temp;
            for (int j = 0; j < len; j++) {
                // push the row elements into the temporary vector
                temp.push_back(arr[i][j]);
            }

            // check row is palidrome or not
            if (checkPalindrome(temp)) {
                // make integer to string using to_string() function and return ans string
                return to_string(i) + " R";
            }
        }

        // Check columns for palindrome
        for (int j = 0; j < len; j++) {
            vector<int> temp;
            for (int i = 0; i < len; i++) {
                temp.push_back(arr[i][j]);
            }

            if (checkPalindrome(temp)) {
                return to_string(j) + " C";
            }
        }

        return "-1";
    }
```

**Time Complexity** `O(n^2)`, where `n` is the length of the matrix.

**Space Complexity** `O(n)`, where `n` is the length of the matrix.

## Optimize code:

```C++
private:
    bool isPalindrome(const vector<int>& v) {
        int left = 0;
        int right = v.size() - 1;

        while (left < right) {
            if (v[left] != v[right]) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }

public:
    string pattern(vector<vector<int>>& arr) {
        int n = arr.size();

        // Check rows
        for (int i = 0; i < n; i++) {
            if (isPalindrome(arr[i])) {
                
                return to_string(i) + " R";
            }
        }

        // Check columns
        for (int j = 0; j < n; j++) {
            vector<int> column;
            for (int i = 0; i < n; i++) {
                column.push_back(arr[i][j]);
            }

            if (isPalindrome(column)) {
                
                return string(j) + " C";
            }
        }

        return "-1";
    }
```

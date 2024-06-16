# Meta String
- Meta strings are strings that can be made equal by swapping exactly one pair of distinct characters in one of the strings.

### Approach
1. Ensure the strings are of equal length.
2. Count the number of positions where characters differ.
3. If there are exactly two positions where characters differ and swapping characters at these positions makes the strings equal, then the strings are meta strings.

```C++
bool checkMeta(string &str1, string &str2) {
    int len1 = str1.length();
    int len2 = str2.length();

    // Meta strings must have equal length
    if (len1 != len2) {
        return false;
    }

    // Count the number of positions with differing characters
    int diffCount = 0;
    int firstDiffPos = -1;
    int secondDiffPos = -1;

    for (int i = 0; i < len1; ++i) {
        if (str1[i] != str2[i]) {
            diffCount++;
            if (diffCount == 1) {
                firstDiffPos = i;
            } else if (diffCount == 2) {
                secondDiffPos = i;
            } else {
                // More than two differences
                return false;
            }
        }
    }

    // Check if exactly two differences were found and swapping makes them equal
    if (diffCount == 2 && str1[firstDiffPos] == str2[secondDiffPos] && str1[secondDiffPos] == str2[firstDiffPos]) {
        return true;
    }

    return false;
}

```

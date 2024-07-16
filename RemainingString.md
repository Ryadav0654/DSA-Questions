# Remaining string:

> Question link:
> https://www.geeksforgeeks.org/problems/remaining-string3515/1

### Approach:

- initialise the cnt variable to 0
- iterate the each element of string
- check if (ch == s[i]) then increment the cnt by 1.
- check if (cnt == count) return substring
- at the end return empty string

### Code:

```C++
    string printString(string s, char ch, int count) {
        // initialise cnt variable 
        int cnt = 0;

        // iterate the each element of string
        for(int i = 0; i < s.length(); i++){
            // check conditions
            if(s[i] == ch){
                ++cnt;
                if(cnt == count) {
                    return s.substr(i+1);
                }
        }

        // return empty string 
        return "";
    }
```

### Complexity Analysis:

- Time Complexity: `O(N)`, where N is the length of the string.

- Space Complexity: `O(1)`, constant space.
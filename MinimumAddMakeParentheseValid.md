# Minimum Add to Make Parentheses Valid

> Question link:https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/?envType=daily-question&envId=2024-10-09

## Code:

```C++
class Solution {
public:
    int minAddToMakeValid(string s) {
        // initialise the open and min_required_cnt to track the count of '(' and required close or open bracket to make the string valid

        int open_cnt = 0;
        int min_required_cnt = 0;
        // iterate through the string
        for(int i =0; i < s.length(); i++){
            // if the current character is '('
            if(s[i] == '('){
                open_cnt++;

            }else if(open_cnt != 0 && s[i] == ')'){// if the current character is ')'

                open_cnt--;

            }else{

                // if the current character is ')'
                min_required_cnt++;

            }
        }

        // return the open_cnt + min_required_cnt
        //min_required_cnt: which is the count of '(' and required close or open bracket to make the string valid
        return  open_cnt+min_required_cnt;
    }
};
```

**Time Complexity:** `O(n)`, where n is the length of the string.
**Space Complexity:** `O(1),` constant space.

## using stack:

### Code:

```C++
class Solution {
public:
    int minAddToMakeValid(string s) {
        stack<char> st;

        for(int i = 0; i< s.length(); i++){
            if(!st.empty()){
                if(st.top() == '(' && s[i] == ')'){
                    st.pop();
                }else {
                    st.push(s[i]);
                }
            }else{
                st.push(s[i]);
            }
        }

        return st.size();
    }
};
```

**Time Complexity:** `O(n)`, where n is the length of the string.
**Space Complexity:** `O(n),` as we are using a stack of size n

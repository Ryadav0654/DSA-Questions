# Minimum Add to Make Parentheses Valid

> Question link:https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/?envType=daily-question&envId=2024-10-09

## Code:

```C++
class Solution {
public:
    int minAddToMakeValid(string s) {
        int open_cnt = 0;
        int close_cnt = 0;
        for(int i =0; i < s.length(); i++){
            if(s[i] == '('){
                open_cnt++;
            }else if(open_cnt != 0 && s[i] == ')'){
                open_cnt--;
            }else{
                close_cnt++;
            }
        }

        return  open_cnt+close_cnt;
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
# Separate Black and White Balls
> Question link: 
https://leetcode.com/problems/separate-black-and-white-balls/description/?envType=daily-question&envId=2024-10-15

> Solution link:https://leetcode.com/problems/separate-black-and-white-balls/editorial/?envType=daily-question&envId=2024-10-15

## Code:
```C++
class Solution {
public:
    long long minimumSteps(string s) {
        long long cnt = 0;
        long long ans = 0;

        for(int i = s.length()-1; i >= 0; i--){
            if(s[i] == '1'){
                ans += cnt;
            }else{
                cnt++;
            }
            
        }

        return ans;
    }
};

```

```text
- Time complexity: O(n), where n is the length of s.
- Space complexity: O(1), constant space.
```
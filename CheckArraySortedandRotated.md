# Check if Array Is Sorted and Rotated

> Question link:
https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/

> Solution link:
https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/solutions/5224249/efficient-easy-to-understand-c-code-beats-100/


### code:
```C++
    bool check(vector<int>&nums){
        int cnt = 0;

        for(int i = 1; i < nums.size(); i++){
            if(nums[i-1] > nums[i]){
                cnt++;
            }
        }

        if(nums[n-1] > nums[0])
            cnt++;

        return cnt <= 1;
    }

```

- Time complexity:` 0(n)`, n is the size of the array

- Space complexity: `0(1)`

# Maximum Subarray:

### Question link: 
> https://leetcode.com/problems/maximum-subarray/description/ 

> https://www.naukri.com/code360/problems/630526?topList=striver-sde-sheet-problems&leftPanelTabValue=PROBLEM

## Code:

```C++
  int maxSubArray(vector<int>& nums) {
    //initialize maxi and sum which track the maximum sum and current sum
    long long maxi = INT_MIN;
    int n = nums.size();
    long long sum = 0;

    //apply kadane's algorithm
    for(int i = 0; i< n; i++){
        sum += nums[i];
        maxi = max(maxi, sum);
        if(sum < 0) sum = 0;
    }

    return maxi;
    }
```

- Time complexity: O(n)
- Space complexity: O(1)

```C++
 int maxSubArray(vector<int>& nums) {
    long long maxi = INT_MIN;

    for(int i =0; i< n; i++){
        long long sum = 0;
        for(int j = i; j < n; j++){
            sum += arr[j];
            maxi = max(maxi, sum);
        }
    }

    return maxi;
 }
```
- Time complexity: O(n^2)
- Space complexity: O(1)
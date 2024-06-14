# Minimum Increment to make Array Unique

> Question link:
> https://leetcode.com/problems/minimum-increment-to-make-array-unique/description/?envType=daily-question&envId=2024-06-14

### Approach:

1. **Sort the input array**: The first step is to sort the input array `nums` in non-decreasing order. Sorting the array allows us to identify duplicate elements efficiently and ensures that we can iterate through the array in a controlled manner.

2. **Iterate through the sorted array**: After sorting, we iterate through the sorted array. We maintain a variable `prev` to keep track of the previous element encountered during the iteration. We start iterating from the second element (index 1) because there's no previous element for the first one.

3. **Check for duplicates and increment if necessary**: For each element in the sorted array, we compare it with the previous element (`prev`). If the current element is less than or equal to the previous one, it indicates a duplicate. In this case, we need to increment the current element to make it greater than the previous one and thus unique. We increment a counter `cnt` to keep track of the total number of increments needed.

4. **Update the previous element**: After handling duplicates, we update the `prev` variable to either the current element (if it's not a duplicate) or the next possible unique value (if it's a duplicate). This ensures that we maintain the correct state for the next iteration.

5. **Return the total count of increments**: After iterating through the entire array, we return the final count `cnt`, which represents the minimum number of increments needed to make all elements in the array unique.

### Code:
```C++
int minIncrementForUnique(vector<int>& nums) {
    sort(nums.begin(), nums.end());
    int cnt = 0;
    int prev = nums[0];
    for(int i = 1; i < nums.size(); i++) {
        if (nums[i] <= prev) {
            cnt += prev - nums[i] + 1; 
            prev = prev + 1; 
        } else {
            prev = nums[i]; 
        }
    }
    return cnt;
    }

```

**Time Complexity:** O(n log n), where `n` is the length of the input array.

**Space Complexity:** O(1), as no extra space is used.

### Method - 2:

**Time limit Exceeded**

**Code:**
```C++
int minIncrementForUnique(vector<int>& nums) {
  
        sort(nums.begin(), nums.end());
        int cnt = 0;
        for(int i = 0; i < nums.size()-1; i++){
        for(int j = i+1; j < nums.size(); j++){
            if(nums[i] == nums[j]){
                nums[j] += 1;
                cnt++;
            }
            }
        }

        return cnt;
    }
```
**Time Complexity:** O(n^2), where `n` is the length of the input array.

**Space Complexity:** O(1), as no extra space is used.
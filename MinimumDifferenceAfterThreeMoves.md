# Minimum Difference Between Largest and Smallest Value in Three Moves:

**Problem Statement**

- You are given an integer array nums.

- In one move, you can choose one element of nums and change it to any value.

- Return the minimum difference between the largest and smallest value of nums after performing at most three moves.

**Example 1:**

- Input: nums = [5,3,2,4]
- Output: 0
- Explanation: We can make at most 3 moves.
- In the first move, change 2 to 3. nums becomes [5,3,3,4].
- In the second move, change 4 to 3. nums becomes [5,3,3,3].
- In the third move, change 5 to 3. nums becomes [3,3,3,3].
- After performing 3 moves, the difference between the minimum and maximum is 3 - 3 = 0.

### Approach:

- if array size if less than 4 return 0
- sort the array
- Evaluate four scenarios
    - Change smallest 3 elements
    - Change largest 3 elements
    - Change smallest 2 elements and largest 1 element
    - Change smallest 1 element and largest 2 elements
- Return the minimum difference among the four scenarios
### Code:

```C++
int minDifference(vector<int>& nums) {
        int n = nums.size();
        if (n <= 4) return 0; // If there are 4 or fewer elements, we can make all elements equal

        sort(nums.begin(), nums.end());

        // Evaluate four scenarios
        int scenario1 = nums[n-4] - nums[0];  // Change smallest 3 elements
        int scenario2 = nums[n-1] - nums[3];  // Change largest 3 elements
        int scenario3 = nums[n-3] - nums[1];  // Change smallest 2 elements and largest 1 element
        int scenario4 = nums[n-2] - nums[2];  // Change smallest 1 element and largest 2 elements

        // Return the minimum difference among the four scenarios
        return min({scenario1, scenario2, scenario3, scenario4});
    }
```

**Time Complexity**
- `O(n*log(n))` to sorting the array, where n is the size of the nums array.

**Space complexity**
- `O(1)` , no space required.

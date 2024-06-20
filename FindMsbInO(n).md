#  Find MSB In O(1) or Greatest Power Of 2 which Is Less Than Or Equal To N

## Problem statement: 
- You are given a positive integer 'N'. Your task is to find the greatest integer less than or equal to 'N' which is a power of 2.

**For Example:**
- If N = 14, then the nearest integer that is less than or equal to 14 and is a power of two is 8(2^3). So, the answer is 8.
**Follow Up:**
- Can you solve this in constant time and space complexity?

### Approach:
1. **Check if \( N \) is a Power of 2:**
   - Use the condition `(N & (N - 1)) == 0` to determine if \( N \) is already a power of 2.
   - If true, return \( N \) immediately because \( N \) itself is the greatest power of 2 less than or equal to \( N \).

2. **Finding the Greatest Power of 2:**
   - Initialize a variable `power` to 1.
   - Use a loop to left-shift `power` (`power <<= 1`) until `power` exceeds \( N \).
   - After exiting the loop, `power` will be the smallest power of 2 that is greater than \( N \).
   - Return `power >> 1` (which is equivalent to `power / 2`) to get the greatest power of 2 less than or equal to \( N \).

### Code:
```C++
int findMSB(int n){
	
    // check n is the power of 2 or not 
	if(n & (n-1) == 0){
		return n;
	}

    // find power of 2 that is greater than n
	int power = 1;
	while(power <= n){
        // left shift
		power <<= 1;
	}

    // return power / 2(right shift)
	return power >> 1;
	
}
```

### Complexity:
- **Time complexity:** This approach ensures constant time complexity \( O(1) \) because the operations involved (bit manipulation and simple arithmetic) are executed in a fixed number of steps, independent of the size of \( N \).
- **Space Complexity:** The space complexity is also \( O(1) \) because only a constant amount of extra space is used (for the `power` variable).



# Padovan Sequence:

> Question link:
> https://www.geeksforgeeks.org/problems/padovan-sequence2855/1

### Approach:

1. **Base Cases Handling**:
   - If ( n ) is 0, 1, or 2, the function returns 1, as per the definition of the Padovan sequence.

2. **Variable Initialization**:
   - Three variables `prev2`, `prev1`, and `current` are initialized to store the last three values of the Padovan sequence.
   - `prev2`, `prev1`, and `current` are initially set to 1, reflecting the base case values.

3. **Iterative Calculation of Padovan Sequence**:
   - Starting from ( i = 3 ) up to ( n ), the function iterates to calculate each value of the Padovan sequence.
   - At each iteration, the next value of the sequence (`next`) is calculated as the sum of the previous two values (`prev2` and `prev1`).
   - The modulo operation is applied to `next` with a large prime number (`1e9 + 7`) to prevent integer overflow and ensure that the result fits within the range of an integer.
   - `prev2`, `prev1`, and `current` are updated accordingly for the next iteration.

4. **Return Result**:
   - After the loop completes, `current` holds the value of the Padovan sequence for ( n ), which is then returned.


### Code:   
```C++
int padovanSequence(int n) {
    // Base cases
    if (n == 0 || n == 1 || n == 2) {
        return 1;
    }
    
    // Initialize variables to store the last three values of the Padovan sequence
     int prev2 = 1, prev1 = 1, current = 1;
    
    // Calculate Padovan sequence values iteratively
    for (int i = 3; i <= n; ++i) {
         int next = prev2 + prev1;
        prev2 = prev1;
        prev1 = current;
        current = next % (int)(1e9 + 7); // Apply modulo operation to prevent overflow
    }
    
    // Return the result for n
    return current;
    }
```
**Time Complexity:** `O(n)`, where `n` is the input value.

**Space Complexity:** `O(1)`, as no extra space is used.

## Method - 2: Using Recursion

### Code:
```C++
int padovanSequence(int n) {
       // base case
        if(n == 0 || n == 1 || n == 2){
            return 1;
        }
        
        //recursive call
        return padovanSequence(n-2) + padovanSequence(n-3);
        
    }
```

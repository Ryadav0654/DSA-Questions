# Boring Factorial:

**Problem Statement**

- You are given an integer ‘N’ and a prime number ‘P’. Your task is to find the N! modulo P.

**Constraints :**

- 1 <= T <= 10
- 1 <= N <= 10^9
- 1 <= P <= 10^9
- |N - P| <= 1000

### Approach:

1. **Check Constraint**:

   - If \( N \geq P \), return 0 immediately because \( P \) divides \( N! \).

2. **Initialize Result**:

   - Start with `result = 1`, as this will be used to accumulate the factorial modulo \( P \).

3. **Iterative Calculation**:

   - Iterate from `i = 2` to `i <= n`.
   - Update `result` as `result = (result * i) % p`.
     - This step calculates the factorial incrementally and takes modulo \( P \) to prevent overflow and keep the numbers manageable.

4. **Early Termination**:

   - During each iteration, check if `result` becomes 0 (`result == 0`).
   - If it does, break out of the loop early.
     - This is a optimization to avoid unnecessary computations once the factorial modulo \( P \) results in 0.

5. **Return Result**:
   - After completing the loop, return the final value of `result`, which represents \( N! \mod P \).

### Code:

```C++
long long boringFactorials(int n, int p)
{
	if(n >= p){
		return 0;
	}

	long long result = 1;
	for(int i = 2; i<= n; ++i){
		result = (result*i)%p;
		if(result == 0){
			break;
		}
	}

	return result;
}

```

**Time Complexity :**
- The function iterates from 2 to \( N \), performing constant-time operations (multiplication and modulo) within each iteration.
- Therefore, the time complexity is \( O(N) \).

**Space Complexity :**
- The function uses a constant amount of extra space \( O(1) \) for storing variables like `result` and `i`.

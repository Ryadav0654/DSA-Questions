# Check Prime Number:

> Question link:
> https://www.geeksforgeeks.org/problems/prime-number2314/1

### Approach(Brute force):

- Enters a loop starting from \( i = 2 \) up to \( i < N \).
- For each value of \( i \), it checks if \( N \) is divisible by \( i \) (i.e., \( N \% i == 0 \)).
- If \( N \) is divisible by \( i \) (meaning \( N \) has a divisor other than 1 and itself), the function immediately returns 0, indicating \( N \) is not a prime number.

### Code:

```C++
int isPrime(int N){
    if(N == 1) return 0;

    for(int i = 2; i < N; i++){
        if(N%i == 0) return 0;
    }

    return 1;
}
```
**Time Complexity:** `O(N)`, where N is the given number.

**Space Complexity** `O(1)` , constant space.

### Approach(Optimal approach):

- Enters a loop starting from \( i = 2 \) up to \( i <= sqrt(N) \).
- For each value of \( i \), it checks if \( N \) is divisible by \( i \) (i.e., \( N \% i == 0 \)).
- If \( N \) is divisible by \( i \) (meaning \( N \) has a divisor other than 1 and itself), the function immediately returns 0, indicating \( N \) is not a prime number.

### Code:

```C++
int isPrime(int N){
    if(N == 1) return 0;

    for(int i = 2; i <= sqrt(N); i++){
        if(N%i == 0) return 0;
    }

    return 1;
}
```
**Time Complexity:** `O(sqrt(N))`, where N is the given number.

**Space Complexity** `O(1)` , constant space.

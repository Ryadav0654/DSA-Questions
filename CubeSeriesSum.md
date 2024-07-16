# Sum of first n terms

> Question link:
> https://www.geeksforgeeks.org/problems/sum-of-first-n-terms5843/1

### Approach:

- use cube sum formula
- summation of n^3 = (n(n+1)/2)^2

### Code:

```C++
    long long sumOfSeries(long long n) {

        long long sum = n*n + n;
        long long ans = (sum*sum)/4;

        return ans;

    }

```

**Time complexity** `O(1)`, because we use formula to solve.

**Space complexity** `O(1)`, const space used.

### Approach(Recursive):

- use cube sum formula
- summation of n^3 = (n(n+1)/2)^2

### Code:

```C++

    long long solve(long long n, long long sum){

        // base case 
        if( n < 1) return sum;

        sum += (n*n*n);

        // recursive call
        return solve(n-1, sum);
    }


    long long sumOfSeries(long long n) {

        return solve(n, 0);

    }

```

**Time complexity** `O(N)`, where N is the is given number.

**Space complexity** `O(N)`, recursive space.



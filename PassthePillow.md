# Pass the pillow:

> Question link:
> https://leetcode.com/problems/pass-the-pillow/description/?envType=daily-question&envId=2024-07-06

### Approach:

- `fullRounds = time / (n - 1)` calculates how many complete rounds of passing occur.
- `extraTime = time % (n - 1)` calculates the remaining time after complete rounds.
- Check if `fullRounds % 2 == 0`:
  - If true, calculate the position as extraTime + 1.
  - If false, calculate the position as n - extraTime.
- Return the position determined in the above step, which indicates the person holding the pillow after time seconds.

### Code:

```C++
    class Solution {
public:
    int passThePillow(int n, int time) {
        // Calculate the number of complete rounds of pillow passing
        int fullRounds = time / (n - 1);

        // Calculate the remaining time after complete rounds
        int extraTime = time % (n - 1);

        // Determine the position of the person holding the pillow
        // If fullRounds is even, the pillow is moving forward.
        // If fullRounds is odd, the pillow is moving backward.
        if (fullRounds % 2 == 0) {
            return extraTime + 1;  // Position when moving forward
        } else {
            return n - extraTime;  // Position when moving backward
        }
    }
};

```

### Code:

```C++
    int passThePillow(int n, int time){
        int div = time/(n-1);
        int rem = time%(n-1);

        if(rem == 0){
            if(div%2 == 0){
                return 1;
            }else{
                return n;
            }
        }else{
            if(div%2 == 0){
                return rem + 1;
            }else{
                return n - rem;
            }
        }
    }
```

**Time complexity:** `O(1)`, constant time complexity.

**Space complexity:** `O(1)`, constant space complexity.

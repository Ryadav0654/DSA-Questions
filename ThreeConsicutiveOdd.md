# Find the three consecutive odd:

**Problem Statement**
- Given an integer array arr, return true if there are three consecutive odd numbers in the array. Otherwise, return false.

**Example**
- Input: arr = [1,2,34,3,4,5,7,23,12]
- Output: true
- Explanation: [5,7,23] are three consecutive odds.

### Approach(Brute Force Approach)
- Iterate over the array till the third last element. For each element:
    - Check if the current and next two elements are all odd
        - If all three elements are odd, return true.
- Return false otherwise.


### Code:
```C++
bool threeConsecutiveOdd(vector<int> &arr){
    int s = arr.size();
    // iterate the arr 
    for(int i = 0; i< s-2; i++){
        // check arr[i] is odd or not
        if(arr[i]&1){
            // check other consecutive elements
            if((arr[i+1]&1) && (arr[i+2]&1)){
                return true;
            }
        }
    }

    return false;
}

```

**Time complexity :** `O(n)`, where `n` is the size of arr.

**Space complexity :** `O(1)`, No extra space used.

### Approach - 2:
- Initialize a variable consecutiveOdds to store the number of consecutive odd numbers during the loop.
- Loop through the given array:
- If the current element is odd, increment consecutiveOdds.
    - If consecutiveOdds is equal to 3, return true.
- Otherwise, reset consecutiveOdds to 0.
- Return false, indicating no three consecutive odds were found.

### Code:
```C++

bool threeConsecutiveOdds(vector<int>&arr){
    int consecutiveOdds = 0;
    for(int num : arr)
    {
        if(num&1){
            ++consecutiveOdds;
            if(consecutiveOdds == 3) {
                return true;
            }
        }else {
            consecutiveOdds = 0;
        }
    }

    return false;
}

```

**Time complexity :** `O(n)`, where `n` is the size of arr.

**Space complexity :** `O(1)`, No extra space used.
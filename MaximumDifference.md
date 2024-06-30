# Find Maximum difference:

**Problem statement:**
- You are given an array 'ARR' of the 'N' element. Your task is to find the maximum difference between any of the two elements from 'ARR'.

- If the maximum difference is even print “EVEN” without quotes. If the maximum difference is odd print “ODD” without quotes.

**For example:**

Given 'ARR' = [1, 10, 5, 2, 8, 1 ] , answer is "ODD".
Here the maximum difference is between 10 and 1, 10 - 1 = 9

### Approach:
- initialize mini and maxi as arr[0]
- iterate through the array and find the max and min values and update the maxi and mini
- return maxi - mini

### Code:

```C++
int maxDiff(int n, vector<int> arr) {
    int maxi = arr[0];
    int mini = arr[0];

    for(int i = 1; i  < n; i++){
        if(arr[i] > maxi){
            maxi = arr[i];
        }else if(arr[i] < mini){
            mini = arr[i];
        }
    }

    return (maxi-mini);
}


string maxDifference(vector<int> arr, int n) {
    int num = maxDiff(n, arr);
    if(num&1) return "ODD";

    return "EVEN";
}

```

### Using inbuilt function:
```C++
string maxDifference(vector<int> arr, int n) {
    int mini = *min_element(arr.begin(), arr.end());
    int maxi = *max_element(arr.begin(), arr.end());
    int num = maxi - mini;
    if(num&1) return "ODD";

    return "EVEN";
}

```

**Time Complexity:** `O(n)`, where `n` is the size of array or vector.

**Space Complexity:** `O(1)`,  constant space.

## Another method:

### Approach:
- sort the array or vector
- return arr[n-1] - arr[0]

### Code:
```C++
    string maxDifference(vector<int>arr, int n){
        sort(arr.begin(), arr.end());
        int num = arr[n-1] - arr[0];

        if(num&1) return "ODD";

        return "EVEN";
    }
```

**Time Complexity:** `O(nlog(n))`, where `n` is the size of array or vector.

**Space Complexity:** `O(1)`,  constant space.
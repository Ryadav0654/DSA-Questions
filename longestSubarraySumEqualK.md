# Longest Subarray with Sum `k` (Using Prefix Sum and Hash Map)

#### Key Concepts:
1. **Prefix Sum**: 
   - The prefix sum at any index `i` is the sum of all elements from the start of the array to index `i`.
   - If the difference between the current prefix sum and the target sum `k` has been seen before, then a subarray with sum `k` exists.

2. **Hash Map**:
   - Use an `unordered_map` (hash map) to store prefix sums and their first occurrence indices.
   - The key of the map is the prefix sum, and the value is the index where this sum was first seen.
   - This allows us to check for subarrays with sum `k` in constant time.

---

### Approach:

1. **Initialize Variables**:
   - `sum`: To keep track of the current running sum of elements.
   - `max_cnt`: To store the length of the longest subarray found with sum `k`.
   - `prefix_sum_map`: A hash map to store the first occurrence of each prefix sum.

2. **Traverse the Array**:
   - For each element `a[i]`, add it to `sum`.
   
3. **Check if the Current Subarray Has Sum `k`**:
   - If `sum == k`, update `max_cnt` to `i + 1`, since the subarray from the start to the current index has sum `k`.
   
4. **Check if the Subarray Ending at Index `i` Has Sum `k`**:
   - If `sum - k` exists in the hash map, it means there is a subarray with sum `k` between the index where `sum - k` was first seen and the current index `i`.
   - Update `max_cnt` if this subarray is longer than the previously found ones.

5. **Store the Current Prefix Sum**:
   - Add the current prefix sum `sum` to the hash map if it hasn't been seen before. This ensures we only store the first occurrence of each prefix sum, which is crucial for finding the longest subarray.

6. **Return `max_cnt`**:
   - After iterating through the array, `max_cnt` will hold the length of the longest subarray with sum `k`.

---

### Code:

```cpp
int longestSubarrayWithSumK(vector<int> a, long long k) {
    unordered_map<long long, int> prefix_sum_map;
    long long sum = 0;
    int max_cnt = 0;

    for (int i = 0; i < a.size(); i++) {
        sum += a[i];
        
        // If the current sum equals k
        if (sum == k) {
            max_cnt = i + 1;  // Subarray from the start to i
        }
        
        // Check if sum - k exists in the map
        if (prefix_sum_map.find(sum - k) != prefix_sum_map.end()) {
            max_cnt = max(max_cnt, i - prefix_sum_map[sum - k]);
        }
        
        // Store the first occurrence of the prefix sum
        if (prefix_sum_map.find(sum) == prefix_sum_map.end()) {
            prefix_sum_map[sum] = i;
        }
    }

    return max_cnt;
}
```

---

### Time and Space Complexity:

- **Time Complexity**: 
  - **O(n)**: The array is traversed once, and each operation involving the hash map (insert, lookup) takes constant time on average.

- **Space Complexity**:
  - **O(n)**: In the worst case, all prefix sums are unique, so the hash map will store `n` entries.

---

### Example Walkthrough:

For the input array `[8, 15, 17, 0, 11]` and `k = 17`:

1. **i = 0**:
   - Current element: 8, `sum = 8`.
   - `sum != k`, store `8` in the hash map.

2. **i = 1**:
   - Current element: 15, `sum = 23`.
   - `sum != k`, store `23` in the hash map.

3. **i = 2**:
   - Current element: 17, `sum = 40`.
   - `sum - k = 40 - 17 = 23`, which exists in the hash map (at index 1).
   - Subarray `[17]` (from index `2` to `2`) has sum `k`. Update `max_cnt = 1`.

4. **i = 3**:
   - Current element: 0, `sum = 40`.
   - `sum - k = 40 - 17 = 23`, exists in the hash map (index 1).
   - Subarray `[17, 0]` (from index `2` to `3`) has sum `k`. Update `max_cnt = 2`.

5. **i = 4**:
   - Current element: 11, `sum = 51`.
   - `sum - k = 51 - 17 = 34` does not exist in the hash map.
   - Store `51` in the hash map.

**Result**: The longest subarray with sum `k = 17` is `[17, 0]`, with a length of 2.

---

### Advantages of Optimized Approach:
- **Efficient**: Reduces the time complexity to O(n) compared to O(n²) in the brute-force approach.
- **Handles Large Arrays**: Can handle larger input sizes efficiently.
- **General Approach**: Works for both positive and negative integers.
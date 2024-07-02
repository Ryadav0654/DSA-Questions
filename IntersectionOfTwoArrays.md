# Intersection of two arrays II:

**Problem statement**
- Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

**Example**

- Example 1:

    - Input: nums1 = [1,2,2,1], nums2 = [2,2]
    - Output: [2,2]
- Example 2:

    - Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
    - Output: [4,9]
    - Explanation: [9,4] is also accepted.

**Constraints:**

> `1 <= nums1.length, nums2.length <= 1000`

> `0 <= nums1[i], nums2[i] <= 1000`

### Approach:
1. **Sort Both Arrays:** Sorting helps in comparing elements of both arrays efficiently. By sorting both arrays, we can then use a two-pointer approach to find common elements.

2. **Initialize Pointers:** Use two pointers i and j to traverse through nums1 and nums2 respectively. 

3. **Traverse Both Arrays:**

- Compare the elements at the current positions of both pointers.
- If the element in nums1 is less than the element in nums2, increment pointer i.
- If the element in nums1 is greater than the element in nums2, increment pointer j.
- If the elements are equal, it means we have found a common element. Store this element in nums1[k], increment i, j, and k.
- Return the Result: The result is stored in the first k positions of nums1. Use Arrays.copyOfRange to return this part of the array.

### Code:

```C++
     vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        // sort the both array
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());

        // initialise the result vector
        vector<int> result;

        // traverse the both array
        int i = 0, j = 0;
        while(i < nums1.size() && j < nums2.size()){
            if(nums1[i] < nums2[j]){
                i++;
            }else if(nums1[i] > nums2[j]){
                j++;
            }else {
                result.push_back(nums1[i]);
                i++;
                j++;
            }
        }

        return result;
     }
```

**Time Complexity:**
- Sorting both arrays takes `(O(n log n + m log m))`, where (n) is the length of nums1 and (m) is the length of nums2. The two-pointer traversal takes `(O(n + m))`. Thus, the overall time complexity is `(O(n log n + m log m + n + m) = O(n log n + m log m))`.

**Space Complexity:**
- The space complexity is `(O(1))` if we ignore the space used for sorting, as we are not using any extra space apart from the input arrays. 

### Follow-up Questions:
1. **What if the given array is already sorted? How would you optimize your algorithm?**

- If the arrays are already sorted, the sorting step can be skipped. This reduces the time complexity to (O(n + m)) for the two-pointer traversal.
2. **What if nums1's size is small compared to nums2's size? Which algorithm is better?**

- If nums1 is much smaller than nums2, using a hash map to count elements in nums1 and then iterating through nums2 to find common elements can be more efficient. This avoids the overhead of sorting the larger array.
3. **What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?**

- If elements of nums2 are stored on disk, a multi-pass approach might be necessary. First, load chunks of nums2 into memory, compare with nums1 (which can be fully loaded if it is small enough), and keep track of the intersection. This can be done using external sorting or streaming techniques.
# sort colors:

> Question link:
> https://leetcode.com/problems/sort-colors/submissions/1285565171/?envType=daily-question&envId=2024-06-12

## Method - 1 : Using Dutch National Flag Algorithm
### Approach:
 `Dutch National Flag algorithm` is used to sort an array containing three different types of elements (colors, in this case) in linear time without using any extra space. 

1. **Initialization**: 
   - Initialize three pointers:
     - `r` (red) starts from the beginning of the array (index 0).
     - `w` (white) starts from the beginning of the array (index 0).
     - `b` (blue) starts from the end of the array (index `nums.size() - 1`).


2. **Loop**:
   - While the `w` pointer is less than or equal to the `b` pointer:
     - If the element at index `w` is 2 (blue), it is out of place and needs to be moved to the blue section. Swap the element at index `w` with the element at index `b`, and decrement `b` to move it towards the beginning of the array.
     - If the element at index `w` is 0 (red), it is also out of place and needs to be moved to the red section. Swap the element at index `w` with the element at index `r`, and increment both `w` and `r` to move them towards the end of the red section.
     - If the element at index `w` is 1 (white), it is already in the correct section, so just increment `w` to move to the next element.

3. **Termination**:
   - The loop terminates when `w` crosses or meets `b`, indicating that all elements have been processed.

4. **Result**:
   - After the loop, the array is partitioned into three sections according to the colors (0, 1, and 2), with all 0s before all 1s, and all 1s before all 2s.

### Code:

```C++
void sortColors(vector<int>& nums) {
       int r = 0;
       int w = 0;
       int b = nums.size() -1;

       while(w <= b){
        if(nums[w] == 2 ){
            swap(nums[w], nums[b]);
            b--;
        }else if(nums[w] == 0){
            swap(nums[r], nums[w]);
            w++;
            r++;
        }else{
            w++;
        }
       }
    }
```

- **Time Complexity:** `O(n)`, where `n` is the length of the array.

- **Space Complexity:** `O(1)`, as no extra space is used.

## Method - 2: Using Counting Sort

### Approach:

1. **Count Occurrences**:
   - Initialize an array `count` of size 3, with all elements initialized to 0. This array will be used to count the occurrences of each color (0, 1, and 2).
   - Iterate through the input array `nums`.
   - For each element in `nums`, increment the corresponding count in the `count` array.

2. **Place Colors Back**:
   - Initialize an index `i` to traverse the `nums` array.
   - Iterate through the `count` array:
     - For each color, repeat the following steps until its count becomes zero:
       - Assign the current color to the `nums[i]`.
       - Increment `i`.
       - Decrement the count of the current color.


### Code:

```C++
void sortColors(vector<int>& nums) {
    int count[3] = {0}; // Initialize an array to count occurrences of each color

    // Count occurrences of each color
    for (int num : nums) {
        count[num]++;
    }

    int i = 0;
    // Place the counted colors back into the array
    for (int color = 0; color < 3; color++) {
        while (count[color]--) {
            nums[i++] = color;
        }
    }
}

```

- **Time Complexity:** `O(n)`, where `n` is the length of the array.

- **Space Complexity:** `O(1)`, as no extra space is used.

## Method - 3: Using standard library sort

### Code:

```C++  

void sortColors(vector<int>& nums) {
    sort(nums.begin(), nums.end());
}
``` 

- **Time Complexity:** `O(n log(n))`, where `n` is the length of the array.

- **Space Complexity:** `O(1)`, as no extra space is used.
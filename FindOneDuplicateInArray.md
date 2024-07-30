# Find the Duplicate Number:

> Question link:
> https://leetcode.com/problems/find-the-duplicate-number/description/

> Solution link:
> https://leetcode.com/problems/find-the-duplicate-number/solutions/1892921/9-approaches-count-hash-in-place-marked-sort-binary-search-bit-mask-fast-slow-pointers

### Approach:
- sort the array and check duplicate elements

### Code:

```C++
 int findDuplicate(vector<int>& nums) {
        sort(nums.begin(), nums.end());

        for(int i = 0; i< nums.size()-1; i++){
            if(nums[i] == nums[i+1]){
                return nums[i];
            }
        }

        return -1;
    }
```

**Time Complexity** `O(N*log(N))`, where N is the size of array or vector.

**Space Complexity** `O(N)`, where N is the size of array or vector.

### Approach 2:
- use unordered_map to count the frequency of each element
- check if frequency of any element greater than 1 return that element 

### Code:

```C++
   int findDuplicate(vector<int>& nums) {
        unordered_map<int, int> m;
        for(int i = 0; i < nums.size(); i++){
            m[nums[i]]++;
        }

        for(int i = 0; i < nums.size(); i++){
            if(m[i] > 1){
                return i;
            }
        }

        return -1;
    }

```

**Time Complexity** `O(N)`, where N is the size of array or vector.

**Space Complexity** `O(N)`, where N is the size of array or vector.
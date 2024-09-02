# Remove Duplicates from Sorted Array

> Question link:
> https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/

> Solution link:
> https://takeuforward.org/data-structure/remove-duplicates-in-place-from-sorted-array/

### Code:

```C++

int removeDuplicates(int arr[], int n) {
  set < int > set;
  for (int i = 0; i < n; i++) {
    set.insert(arr[i]);
  }
  int k = set.size();
  int j = 0;
  for (int x: set) {
    arr[j++] = x;
  }
  return k;
}

```

- Time complexity:` O(n*log(n))+O(n)`

- Space Complexity: `O(n) `

### Code:

```C++
   int removeDuplicates(vector<int>& nums) {
        vector<int> ans;
        for(int i = 1; i < nums.size(); i++){
            // if elements are not equal then push them in ans
            if((nums[i-1]^nums[i]) != 0){
                ans.push_back(nums[i-1]);
            }
        }

        // push the last element
        ans.push_back(nums[nums.size()-1]);

        // copy ans to nums
        nums = ans;
        return ans.size();
    }

```

**Time Complexity** `O(N)`, where N is the size of array or vector.

**Space Complexity** `O(N)`, where N is the size of array or vector.

## Optimal approach(two pointer algorithm):

### Code:

```C++
    int findDuplicate(vector<int>& nums) {
        int j = 0;
        for(int i = 1; i < nums.size(); i++){
            // if elements are not equal then push them in ans
            if((nums[j]^nums[i]) != 0){
                j++;
                nums[j] = nums[i];
            }
        }

        return j+1;
    }
```

**Time Complexity** `O(N)`, where N is the size of array or vector.

**Space Complexity** `O(1)`, where N is the size of array or vector.

# Sort the people:

### Problem Statement:

- You are given an array of strings names, and an array heights that consists of distinct positive integers. Both arrays are of length n.

- For each index i, names[i] and heights[i] denote the name and height of the ith person.

- Return names sorted in descending order by the people's heights.

> Editorial link:
> https://leetcode.com/problems/sort-the-people/editorial

### Approach:

- iterate the heights array and sort with the names array

### Code:

```C++
    vector<string> sortPeople(vector<string>& names, vector<int>& heights) {
        int n = heights.size();

        for(int i = 0; i < n-1; i++){
            for(int j = i+1; j < n; j++){
                if(heights[i] < heights[j]){
                    swap(heights[i], heights[j]);
                    swap(names[i], names[j]);
                }
            }
        }

        return names;
    }
```

### Complexity Analysis:

**Time Complexity:** `O(n^2)`, where n is the size of the heights ar names array or vector.

**Space Complexity:** `O(1)`

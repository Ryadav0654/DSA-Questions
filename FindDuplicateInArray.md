# Find duplicate in Array(More than one elements are duplicate):

> Question link:
> https://www.geeksforgeeks.org/problems/find-duplicates-in-an-array/1

### Approach:

1. **Counting Occurrences**:
   - Initialize a vector `cnt` of size `n` and initialize all elements with 0. This vector will be used to count the occurrences of each element in the input array `arr`.
   - Iterate through the array `arr`.
   - For each element `arr[i]`, increment the count of `arr[i]` in the `cnt` vector.

2. **Finding Duplicates**:
   - Initialize an empty vector `ans` to store indices of elements with counts greater than 1.
   - Iterate through the `cnt` vector:
     - If the count of an element at index `j` is greater than 1, push `j` (which represents the element) into the `ans` vector.

3. **Handling Empty Result**:
   - If the `ans` vector is empty, it means there are no duplicates. In this case, return a vector containing only `-1`.

4. **Return Result**:
   - Otherwise, return the `ans` vector containing indices of duplicate elements.


### Code:

```C++
vector<int> duplicates(long long arr[], int n) {

        //create a count vector of size n and initialize it with 0
        vector<int> cnt(n, 0);

        // store the count of each element in the vector
        for(int i = 0; i < n; i++)
        {
            cnt[arr[i]]++;
        }

        // create an ans vector and store all the indices in which the count is greater than 1
        vector<int> ans;
        for(int j = 0; j < cnt.size(); j++){
            if(cnt[j] > 1){
                ans.push_back(j);
            }
        }

        // if the ans vector is empty return {-1}
        if(ans.size() == 0) {
            return {-1};
        }

        return ans;
    }
```

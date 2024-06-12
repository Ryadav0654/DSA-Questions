# Find duplicate in Array:

> Question link:
> https://www.geeksforgeeks.org/problems/find-duplicates-in-an-array/1

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

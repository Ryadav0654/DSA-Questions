# Height Checker:

> Question link:
> https://leetcode.com/problems/height-checker/description/?envType=daily-question&envId=2024-06-10

### Appoach:

- copy the given heights vector into the temp vector
- sort the temp vector
- check the condition (heights[i] != temp[i]) and increment the cnt
- return the cnt

### Code:

```C++
int heightChecker(vector<int>& heights) {
        //copy vector
        vector<int> temp;
        for(int i = 0; i < heights.size(); i++){
            temp.push_back(heights[i]);
        }

        // or vector<int> temp = heights;
        
        //sort the temp vector
        sort(temp.begin(), temp.end());

        //check the indicies place correct or not
        int cnt = 0;
        for(int i = 0; i < heights.size(); i++){
            if(heights[i] != temp[i]){
                cnt++;
            }
        }

        // return the ans
        return cnt;

    }

```

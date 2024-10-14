# Maximal Score After Applying K Operations

> Question link: https://leetcode.com/problems/maximal-score-after-applying-k-operations/description/?envType=daily-question&envId=2024-10-14


## Code: 

```C++
class Solution {
public:
    long long maxKelements(vector<int>& nums, int k) {
        priority_queue<int> pq;
        long long score = 0;
        for(auto i: nums){
            pq.push(i);
        }

        while(k--){
            double ele = pq.top();  
            pq.pop(); 
            score += ele; 
            pq.push((ceil(ele/3)));
            
        }
        return score;
    }
};

```

```text
- Time Complexity: O(nlogn), where n is the length of nums
- Space Complexity: O(n), where n is the length of nums

```
# Find the center node of Star graph:

> Question link:
> https://leetcode.com/problems/find-center-of-star-graph/description/?envType=daily-question&envId=2024-06-27

- Note :The given edges represent a valid star graph.

### Approach:

- center node is the node which is connected to all other nodes in the graph.
- take first two edges and check which node is connected to both edges.
- return that node.

### Code:

**first code**

```C++
 private:
 // take two edges and check which node is connected to both edges.
    int commonNode(vector<int> first, vector<int> second){
        int common_node = -1;
        for(int i =0 ; i < 2; i++){
            if(first[i] == second[0] || first[i] == second[1]){
                common_node = first[i];
            }
        }
        return common_node;
    }

public:
    int findCenter(vector<vector<int>>& edges) {
        // return common node
        int ans = commonNode(edges[0], edges[1]);
        return ans;

    }
```

**Second Code:**
- using XOR operator

```C++
    int findCenter(vector<vector<int>>& edges) {
            if((edges[0][0]^edges[1][0]) == 0 || (edges[0][0]^edges[1][1]) == 0){
                return edges[0][0];
            }else if((edges[0][1]^edges[1][0]) == 0 || (edges[0][1]^edges[1][1]) == 0){
                return edges[0][1];
            }

            return -1;
    }

```
**Third Code:**

```C++
    int findCenter(vector<vector<int>>& edges) {
            if((edges[0][0] == edges[1][0]) || (edges[0][0] == edges[1][1])){
                return edges[0][0];
            }

            return edges[0][1];
    }

```
**Time Complexity :** `O(1)` constant time complexity

**Space Complexity :** `O(1)` constant space

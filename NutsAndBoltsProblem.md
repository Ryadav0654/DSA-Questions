# Nuts and Bolts Problem

> Question link:
> https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431/1

### Approach:
Here's the approach of the given code:

1. **matchPairsHelper Function**:
   - This function is a recursive helper function used to match pairs of nuts and bolts.
   - It takes as input:
     - `nuts[]`: Array of nuts.
     - `bolts[]`: Array of bolts.
     - `low`: The starting index of the current sub-array.
     - `high`: The ending index of the current sub-array.
     - `order`: A vector representing the order in which nuts and bolts are matched.
   - It performs the following steps:
     - If `low` is less than `high`, proceed with partitioning and matching.
     - Choose the last element of bolts (highest index) as the pivot to partition nuts.
     - Partition nuts based on the pivot element.
     - Partition bolts based on the pivot element obtained from nuts.
     - Recursively match pairs in the left and right sub-arrays.

2. **partition Function**:
   - This function is used to partition the array based on the pivot element.
   - It takes as input:
     - `arr[]`: The array to be partitioned (nuts or bolts).
     - `low`: The starting index of the current sub-array.
     - `high`: The ending index of the current sub-array.
     - `pivot`: The pivot element used for partitioning.
     - `order`: A vector representing the order in which nuts and bolts are matched.
   - It performs the following steps:
     - Initialize `i` to `low`.
     - Iterate through the array from `low` to `high - 1`.
     - If the element at index `j` is less than the pivot according to the order vector, swap it with the element at index `i` and increment `i`.
     - If the element at index `j` is equal to the pivot, swap it with the last element (at index `high`) to move it to its correct position.
     - Finally, swap the pivot element with the element at index `i` to place the pivot in its correct position.
     - Return the index of the pivot element after partitioning.

3. **matchPairs Function**:
   - This function is the public interface for matching pairs of nuts and bolts.
   - It takes as input:
     - `n`: The size of the arrays `nuts[]` and `bolts[]`.
     - `nuts[]`: Array of nuts.
     - `bolts[]`: Array of bolts.
   - It initializes the order vector based on the specified order of elements (characters).
   - Calls the `matchPairsHelper` function with appropriate parameters to match pairs of nuts and bolts.
   
### Code:

```C++
class Solution {
    private:
    void matchPairsHelper(char nuts[], char bolts[], int low, int high, vector<char>& order) {
        if (low < high) {
            // Choose the last element of bolts as pivot to partition nuts
            char pivot = bolts[high];
            int pivotIndex = partition(nuts, low, high, pivot, order);

            // Now nuts[pivotIndex] is in correct place, use it as pivot to partition bolts
            partition(bolts, low, high, nuts[pivotIndex], order);

            // Recursively match pairs in left and right sub-arrays
            matchPairsHelper(nuts, bolts, low, pivotIndex - 1, order);
            matchPairsHelper(nuts, bolts, pivotIndex + 1, high, order);
        }
    }

    int partition(char arr[], int low, int high, char pivot, vector<char>& order) {
        int i = low;
        for (int j = low; j < high; j++) {
            if (find(order.begin(), order.end(), arr[j]) < find(order.begin(), order.end(), pivot)) {
                swap(arr[i], arr[j]);
                i++;
            } else if (arr[j] == pivot) {
                swap(arr[j], arr[high]);
                j--;
            }
        }
        swap(arr[i], arr[high]);
        return i;
    }

  public:

    void matchPairs(int n, char nuts[], char bolts[]) {
         vector<char> order = { '!', '#', '$', '%', '&', '*', '?', '@', '^' };
        matchPairsHelper(nuts, bolts, 0, n - 1, order);
    }
};
```

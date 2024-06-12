# Nuts and Bolts Problem

> Question link:
> https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431/1

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

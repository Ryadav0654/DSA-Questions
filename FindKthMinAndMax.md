# Find kth min and max

> Question link:
> https://www.naukri.com/code360/problem-of-the-day/easy

### Approach:

* Sort the array using standard library sort function 
* Find kth smallest and kth largest element in the array
* insert them in a ans vector 
* Return them in a vector

### Code:

```C++
vector<int> kthSmallLarge(vector<int> &arr, int n, int k)
{
	sort(arr.begin(), arr.end());
	int kSmallest = arr[k-1];
	int kLargest = arr[n-k];

	vector<int> ans;
	ans.push_back(kSmallest);
	ans.push_back(kLargest);

	return ans;
}
```

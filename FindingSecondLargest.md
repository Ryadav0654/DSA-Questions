# Finding second largest element of the array without sorting:

> Question link:
> https://www.geeksforgeeks.org/problems/second-largest3735/1

### Approach:
- first we find the largest element and then we find the second largest element.

### Code:

```C++
    int print2largest(vector<int> &arr) {
        // Initialise the first and second max variable to store the first and second maximum element
        int first_max = arr[0];
        int second_max = -1;
        
        // iterate the array and find the first largest element
        for(int i : arr){
            if(first_max < i){
                first_max = i;
            }
        }
        
        // iterate the array and find the second largest element 
        for(int i : arr){

            // condition for finding the second largest element
            if(i > second_max && i < first_max){
                second_max = i;
            }
        }
        
        // return the second largest element
        return second_max;
    }
```

**Time complexity** `O(N)`, where N is the size of the array.

**Space complexity** `O(1)`, no extra space needed.

### Second Code:
```C++
    int print2largest(vector<int> &arr) {
        // Initialise the first and second max variable to store the first and second maximum element
        int first_max = arr[0];
        int second_max = -1;
        
        // iterate the array and find the first largest element
        for(int i : arr){
            if(first_max < i){
                first_max = i;
            }
        }
        
        while(first_max != 0){
            --first_max;
        // iterate the array and find the second largest element 
        for(int i : arr){
           
            if(i == first_max){
                second_max = i;
                return second_max;
            }
        }
        }
        // return the second largest element
        return second_max;
    }
```

**Time complexity** `O(N^2)`, where N is the size of the array.

**Space complexity** `O(1)`, no extra space needed.

### Using sorting: 
```C++
    int print2largest(vector<int> &arr) {

        // sort the array 
        sort(arr.begin(), arr.end());

        int second_max = arr[n-2];

        // return the second largest element
        return second_max;
    }
```

**Time complexity** `O(N*log(N))`, where N is the size of the array.

**Space complexity** `O(1)`, no extra space needed.
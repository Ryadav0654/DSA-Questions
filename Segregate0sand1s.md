# Segregate 0s and 1s:

>Question link:
> https://geeksforgeeks.org/problems/segregate-0s-and-1s5106/1

### Approach:

1. **Initialization**: 
   - Initialize two pointers, `i` starting at the beginning (`0`) and `j` starting at the end (`arr.size() - 1`) of the vector `arr`.

2. **Two-pointer Technique**:
   - Use a while loop that continues as long as `i` is less than `j`.
   - Inside the loop:
     - If `arr[i]` is `0`, move `i` to the right `i++`.
     - If `arr[j]` is `1`, move `j` to the left `j--`.
     - If `arr[i]` is `1` and `arr[j]` is `0`, swap `arr[i]` and `arr[j]`, then move `i` to the right `i++` and `j` to the left `j--`.

### Code:
```C++
void segregate0and1(vector<int> &arr){

    int left = 0;
    int right = arr.size() -1;

    while(left < right){

        if(arr[left] == 0){
            left++;
        }else if(arr[right] == 1){
            right--;
        }else{
            swap(arr[left], arr[right]);
            left++;
            right--;
        }
    }

}
```

### Complexity:

- **Time Complexity**: `O(n)`, where n is the number of elements in `arr`. 
- **Space Complexity**: `O(1)`, constant space.
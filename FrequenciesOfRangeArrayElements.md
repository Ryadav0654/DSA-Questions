# Frequencies of limited range array element:

> Question link:
> https://www.geeksforgeeks.org/problems/frequency-of-array-elements-1587115620/0

### Code:

```C++

    //Function to count the frequency of all elements from 1 to N in the array.
    void frequencyCount(vector<int>& arr,int N, int P)
    {
        // code here
        int i = 0;
        while (i<N)
        {
            // If this element is already processed,
            // then nothing to do
            if (arr[i] <= 0 || arr[i]>N || arr[i]>P)
            {
                i++;
                continue;
            }

            // Find index corresponding to this element
            // For example, index for 5 is 4
            int elementIndex = arr[i]-1;

            // If the elementIndex has an element that is not
            // processed yet, then first store that element
            // to arr[i] so that we don't lose anything.
            if (arr[elementIndex] > 0)
            {
                arr[i] = arr[elementIndex];

                // After storing arr[elementIndex], change it
                // to store initial count of 'arr[i]'
                arr[elementIndex] = -1;
            }
            else
            {
                // If this is NOT first occurrence of arr[i],
                // then decrement its count.
                arr[elementIndex]--;

                // And initialize arr[i] as 0 means the element
                // 'i+1' is not seen so far
                arr[i] = 0;
                i++;
            }
        }
        for(int i=0;i<N;i++) {
            if(arr[i] < 0) arr[i] = -arr[i];
            else arr[i]=0;
        }
    }


```

**Time Complexity:** `O(N)`, where N is the size of array.

**Space complexity:** `O(1)`, no extra space required.
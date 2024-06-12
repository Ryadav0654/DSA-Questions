# Statics from a large sample

### Approach:

1. **Construct Sample Array and Find Mode**:
   - Iterate through the `count` vector to construct the sample array and find the mode index (`minIndex`).
   - While iterating, keep track of the total count of elements (`totalCount`) and the total sum of the sample elements (`totalSum`).
   - At each index, if the count of elements is greater than the maximum count (`maxCount`), update `maxCount` and `minIndex`.
   - Construct the sample array by adding the elements according to their counts.

2. **Calculate Basic Statistics**:
   - Find the minimum value by accessing the first element of the sample array (`sample.front()`).
   - Find the maximum value by accessing the last element of the sample array (`sample.back()`).
   - Calculate the mean by dividing the total sum of elements (`totalSum`) by the total count of elements (`totalCount`).

3. **Calculate Median**:
   - If the total count of elements (`n`) is even, calculate the median as the average of the middle two elements of the sample array.
   - If the total count of elements is odd, the median is the middle element of the sample array.

4. **Return Results**:
   - Construct and return a vector `ans` containing the calculated minimum, maximum, mean, median, and mode.


### Code:

```C++
// optimize code
vector<double> sampleStats(vector<int> &count) {
    vector<int> sample;
    int minIndex = 0;
    int maxCount = 0;
    int totalCount = 0;
    double totalSum = 0;

    // Construct sample array and find mode index
    for (int i = 0; i < count.size(); ++i) {
        totalCount += count[i];
        totalSum += i * count[i];
        if (count[i] > maxCount) {
            maxCount = count[i];
            minIndex = i;
        }
        while (count[i]--)
            sample.push_back(i);
    }

    vector<double> ans;

    // find min
    ans.push_back(sample.front());

    // find max
    ans.push_back(sample.back());

    // find mean
    double mean = totalSum / totalCount;
    ans.push_back(mean);

    // find median
    double median;
    int n = sample.size();
    if (n % 2 == 0)
        median = (sample[n / 2] + sample[n / 2 - 1]) / 2.0;
    else
        median = sample[n / 2];
    ans.push_back(median);

    // find mode
    ans.push_back(minIndex);

    return ans;
}


```

```C++
double sum(vector<int>& sample){
    double initialSum = 0;
    for(double i: sample){
        initialSum += i;
    }

    return initialSum;
}

vector<double> sampleStats(vector<int> &count)
{
    vector<int> sample;
    int minIndex = 0;
    for(int i = 0; i < count.size(); i++){

        if(count[minIndex] < count[i]){
            minIndex = i;
        }

        int temp = count[i];
        if(temp != 0){
            while(temp--){
                sample.push_back(i);
            }
        }
    }

    vector<double> ans;
    int ss = sample.size();

    // find min
    double min = sample[0];
    ans.push_back(min);

    //find max
    double max = sample[ss-1];
    ans.push_back(max);

    //find mean
    double totalSum = sum(sample);
    double mean = totalSum/ss;

    ans.push_back(mean);

    //find meadian
    if(ss % 2 == 0){
        double median = (double)(sample[ss/2] + sample[ss/2 -1])/2;
        ans.push_back(median);
    }else{
        int mid = ss/2;
        ans.push_back(sample[mid]);
    }

    // find mode
    ans.push_back(minIndex);

    return ans;

}

```

# Statics from a large sample

> Question link:
> https://www.naukri.com/code360/problem-of-the-day/moderate

`optimize this code`
### Code:

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

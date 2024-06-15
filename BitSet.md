# Bit set:

### Approach:
- create a vector of size 11 and initialize it with 0
- iterate through the string
- count the occurrence of each digit and store it in the vector 
- return the first digit that appears once

### Code:

```C++
int findFirstRepeatingDigit(string digitPattern) {
    // find the length of string
    int n = digitPattern.length();
    // create ans vector and initialize it with 0
    vector<int> ans(11, 0);

    //iterate through the string
    for(int i = 0; i < n; i++){
        // convert char to int
        int a =  digitPattern[i]-'0';
        if(ans[a] == 1){
            return a;
        }else{
            ans[a]++;
        }
    }

    // if no repeating digit is found
    return -1;
}
```

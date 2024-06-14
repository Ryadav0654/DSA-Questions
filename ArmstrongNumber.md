# Armstrong Number:

> Question link:
> https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1


### Code:

```C++
class Solution {
    private:
    int getCube(int a){
        return (a*a*a);
    }

  public:
    string armstrongNumber(int n){
        int num = n;
        int sum = 0;
        while(num != 0){
            int a = num%10;
            sum += getCube(a);
            num /= 10;
        }

        if(sum == n){
            return "Yes";
        }

       return "No";
    }
};
```

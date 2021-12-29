Problem statement: https://www.geeksforgeeks.org/dynamic-programming-building-bridges/

```
#include <bits/stdc++.h>
using namespace std;

struct City {
    int north;
    int south;
};

bool compare(City a,City b){
    if (a.south == b.south)
        return a.north < b.north;
    return a.south < b.south;
}

int maxBridges(City values[],int n)
{
    sort(values,values+n,compare);
    int ans=1;
    vector<int> dp(n,1);
    for(int i=1;i<n;i++) {
        for(int j=0;j<i;j++) {
            if(values[i].north > values[j].north ) {
                dp[i] = max(dp[i], dp[j]+1);
            }
        }
        if(ans < dp[i])ans=dp[i];
    }
    return ans;
}

int main()
{
    City values[] = {{6, 2}, {4, 3}, {2, 6}, {1, 5}};
    int n = 4;
    cout << "Maximum number of bridges = "
             << maxBridges(values, n);   
    return 0;
}
```

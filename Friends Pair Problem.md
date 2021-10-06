# Friends Pairing Problem

Given n friends, each one can remain single or can be paired up with some other friend. Each friend can be paired only once. Find out the total number of ways in which friends can remain single or can be paired up. 

Approach:
Thier are two ways :
1. If single so try to find how n-1 are being paired
2. if paired so try so he can pair with any of n-1 people + how many ways other n-2 are being paired

`f(n) = f(n-1)+ (n-1) * f(n-2)`

```
#include <bits/stdc++.h>
using namespace std;

int findways(int n)
{
    vector<int> dp(n+1,0);
    dp[1]=1;
    dp[2]=2;
    for(int i=3;i<=n;i++)
    {
        dp[i]=dp[i-1]+ (i-1) * dp[i-2];
    }
    return dp[n];
}

int main()
{
    int n;
    cin>>n;
    cout<<findways(n);
}
```

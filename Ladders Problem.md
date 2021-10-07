# Ladders Problem

There are n stairs, a person standing at the bottom wants to reach the top. The person can climb k stairs at a time. Count the number of ways, the person can reach the top.
1D - DP


## Top-Down Approach

```
#include <bits/stdc++.h>
using namespace std;

int findways(int n,int k,int dp[])
{
    if(n==0)return 1;
    if(dp[n]!=0)return dp[n];
    int ways = 0;
    for(int i=1;i<=k;i++)
    {
        if(n-i >=0){
            ways+=findways(n-i,k,dp);
        }
    }
    return ways;
}

int main()
{
    int n,k;
    cin>>n>>k;
    int dp[100] = {0};
    cout<<findways(n,k,dp);
}
```

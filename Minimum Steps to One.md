# Minimum Steps to One


Q. You are given a number, return minimum number of steps needed to convert it into one . Operation if i % 2==0 then i/2, if i%3==0 then i/3 or i=1?


- Using Bottom up approach
- Recurrence Relation: f(n) = min{ f(n/2), f(n/3), f(n-1) };

```
#include <bits/stdc++.h>
using namespace std;

int find(int n)
{
    vector<int> dp(n+1,0);
    for(int i=2;i<=n;i++)
    {
        dp[i] = min({i%2==0?dp[i/2]:INT_MAX , i%3==0?dp[i/3]:INT_MAX , dp[i-1]} ) + 1;
    }
    return dp[n];
}

int main()
{
    int n;
    cin>>n;
    cout<<find(n);
}
```

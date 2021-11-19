Problem Statement: https://www.geeksforgeeks.org/minimum-number-of-squares-whose-sum-equals-to-given-number-n/

```
#include <bits/stdc++.h>
using namespace std;

int find(int n)
{
    vector<int> dp(n+1,10000);
    dp[0]=0;
    dp[1]=1;
    for(int i=2;i<=n;i++)
    {
        int min = 10000;
        for(int j=1;j*j<i;j++)
        {
            int rem = i - j*j;
            if(dp[rem] < min)min=dp[rem];
        }
        dp[i] = min+1;
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

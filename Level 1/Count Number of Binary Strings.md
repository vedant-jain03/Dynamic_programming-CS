# Count Number of Binary Strings

Given n return number of binary string which not have consicutive 1
ex: n = 3 answer: 5
000 001 010 100 101

Approach: We will try to find ways how many ways is there to make binary string if lastdigit is 0 or 1

- for 0 it will be string which ended up with 1 or 0
- for 1 it will be string which ended up with 0 only

### Bottom-up Approach
```
#include <bits/stdc++.h>
using namespace std;

int find(int n)
{
    vector<vector<int>> dp(2,vector<int> (n+1,0));
    dp[0][1] = 1;
    dp[1][1] = 1;
    for(int i=2;i<=n;i++)
    {
        dp[0][i] = dp[0][i-1]+dp[1][i-1];
        dp[1][i] = dp[0][i-1];
    }
    return dp[0][n]+dp[1][n];
}

int main()
{
    int n;
    cin>>n;
    cout<<find(n);
}
```

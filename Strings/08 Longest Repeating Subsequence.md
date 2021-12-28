Problem statement: https://www.geeksforgeeks.org/longest-repeating-subsequence/

```
#include <bits/stdc++.h>
using namespace std;

int find(string x,string y)
{
    int n=x.size();
    int m=y.size();
    int ans=0;
    vector<vector<int>> dp(n+1, vector<int>(m+1,0));
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=m;j++)
        {
            if(x[i-1]==y[j-1] && i!=j) {
                dp[i][j] = 1+dp[i-1][j-1];
            }
            else {
                dp[i][j]=max(dp[i-1][j], dp[i][j-1]);
            }
        }
    }
    return dp[n][m];
}

int main()
{
    string x;
    cin>>x;
    cout<<find(x,x);
}

```

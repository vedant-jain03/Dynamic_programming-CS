Problem solving: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/longest-common-substring-official/ojquestion

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
            if(x[i-1] == y[j-1]) {
                dp[i][j]=1+dp[i-1][j-1];
            }
            ans = max(ans,dp[i][j]);
        }
    }
    return ans;
}

int main()
{
    string x;
    cin>>x;
    string y;
    cin>>y;
    cout<<find(x,y);
}

```

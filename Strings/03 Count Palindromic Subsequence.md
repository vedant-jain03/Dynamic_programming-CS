Problem statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/cps-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

int find(string s)
{
    int n=s.size();
    vector<vector<int>> dp(n, vector<int>(n));
    for(int g=0;g<n;g++)
    {
        for(int i=0,j=g;j<n;i++,j++)
        {
            if(g==0) dp[i][j] = 1;
            else if(g==1) {
                if(s[i] == s[j]) dp[i][j]=3;
                else dp[i][j]=2;
            }
            else {
                if(s[i] == s[j]) dp[i][j] = dp[i+1][j]+dp[i][j-1]+1;
                else dp[i][j] = dp[i+1][j]+dp[i][j-1]-dp[i+1][j-1];
            }
        }
    }
    return dp[0][n-1];
}

int main()
{
    string s;
    cin>>s;
    cout<<find(s);
}
```

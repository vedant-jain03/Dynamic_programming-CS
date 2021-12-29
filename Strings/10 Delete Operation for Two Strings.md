Problem statement: https://leetcode.com/problems/delete-operation-for-two-strings/

```
class Solution {
public:
    int minDistance(string x, string y) {
        int n=x.size(),m=y.size();
        vector<vector<int>> dp(n+1,vector<int> (m+1,0));
        for(int i=1;i<=n;i++)
        {
            for(int j=1;j<=m;j++)
            {
                if(x[i-1] == y[j-1]) {
                    dp[i][j] = 1+dp[i-1][j-1];
                }
                else {
                    dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
                }
            }
        }
        int lcs = dp[n][m];
        int a = abs(n-lcs);
        int b = abs(m-lcs);
        return a+b;
    }
};
```

Problem statement: https://leetcode.com/problems/longest-palindromic-subsequence/

```
class Solution {
public:
    int LCS(string x,string y)
    {
        int n=x.size();
        int m=y.size();
        vector<vector<int>> dp(n+1,vector<int>(m+1));
        for(int i=1;i<=n;i++)
        {
            for(int j=1;j<=m;j++)
            {
                if(x[i-1] == y[j-1]) {
                    dp[i][j] = 1+dp[i-1][j-1];
                }
                else {
                    dp[i][j] = max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return dp[n][m];
    }
    int longestPalindromeSubseq(string s) {
        string x=s;
        reverse(s.begin(),s.end());
        return LCS(x,s);
    }
};
```

Problem statement: https://leetcode.com/problems/wildcard-matching/

```
class Solution {
public:
    bool isMatch(string s, string p) {
        int n=s.size();
        int m=p.size();
        vector<vector<bool>> dp(m+1,vector<bool>(n+1,false));
        for(int i=dp.size()-1;i>=0;i--)
        {
            for(int j=dp[0].size()-1;j>=0;j--)
            {
                if(i==dp.size()-1 && j==dp[0].size()-1) dp[i][j]=true;
                else if(i==dp.size()-1) dp[i][j]=false;
                else if(j==dp[0].size()-1) {
                    if(p[i]=='*')dp[i][j]=dp[i+1][j];
                }
                else {
                    if(p[i] == '?') {
                        dp[i][j] = dp[i+1][j+1];
                    }
                    else if(p[i] == '*') {
                        dp[i][j] = dp[i+1][j] || dp[i][j+1];
                    }
                    else if(p[i] == s[j]) {
                        dp[i][j] = dp[i+1][j+1];
                    }
                    else {
                        dp[i][j] = false;
                    }
                }
            }
        }
        return dp[0][0];
    }
};
```

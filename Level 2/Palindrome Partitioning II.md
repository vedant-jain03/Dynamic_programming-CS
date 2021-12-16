# Problem statement: https://leetcode.com/problems/palindrome-partitioning-ii/submissions/

```
class Solution {
public:
    int minCut(string s) {
        int n=s.length();
        bool dp[n][n];
        for(int g=0;g<n;g++)
        {
            for(int i=0,j=g;j<n;i++,j++)
            {
                if(g==0)dp[i][j]=true;
                else if(g==1) {
                    if(s[i] == s[j])dp[i][j]=true;
                    else dp[i][j]=false;
                }
                else {
                    if(s[i] == s[j] && dp[i+1][j-1]==true)dp[i][j]=true;
                    else dp[i][j]=false;
                }
            }
        }
        int ans[n];
        ans[0]=0;
        for(int j=1;j<n;j++)
        {
            if(dp[0][j] == true) {
                ans[j]=0;
                continue;
            }
            int res=INT_MAX;
            for(int i=j;i>=1;i--)
            {
                if(dp[i][j]==true) {
                    if(ans[i-1] < res)res=ans[i-1];
                }
            }
            ans[j] = res+1;
        }
        return ans[n-1];
    }
};
```

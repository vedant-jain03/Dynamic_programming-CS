Problem statement: https://leetcode.com/problems/longest-palindromic-substring/

```
class Solution {
public:
    string longestPalindrome(string s) {
        int n=s.size();
        bool dp[n][n];
        int start=-1;
        int max=INT_MIN;
        for(int g=0;g<n;g++)
        {
            for(int i=0,j=g;j<n;i++,j++)
            {
                if(g==0) {
                    dp[i][j] = true;
                }
                else if(g==1) {
                    dp[i][j] = (s[i]==s[j]);
                }
                else {
                    if(s[i]==s[j] && dp[i+1][j-1]) dp[i][j]=true;
                    else dp[i][j]=false;
                }
                if(dp[i][j]) {
                    if(max < g) {
                        max=g;
                        start=i;
                    }
                }
            }
        }
        string ans = s.substr(start, max+1);
        return ans;
    }
};
```

# Minimum Coin Change

```
class Solution {
public:
    int coinChange(vector<int>& coins, int n) {
        vector<int> dp(n+1,10000);
        dp[0]=0;
        for(int i=1;i<=n;i++)
        {
            for(int j=0;j<coins.size();j++)
            {
                if(i-coins[j]>=0)
                {
                    dp[i] = min(dp[i], dp[i-coins[j]]+1);
                }
            }
        }
        return dp[n]>=10000?-1:dp[n];
    }
};
```

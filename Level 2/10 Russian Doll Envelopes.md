Problem statement: https://leetcode.com/problems/russian-doll-envelopes/

```
class Solution {
public:
    int maxEnvelopes(vector<vector<int>>& arr) {
        sort(arr.begin(),arr.end());
        int n = arr.size();
        vector<int> dp(n,1);
        int ans = 1;
        for(int i=1;i<n;i++) {
            for(int j=0;j<i;j++)
            {
                if(arr[i][1] > arr[j][1] && arr[i][0]!=arr[j][0]) {
                    dp[i] = max(dp[i], dp[j]+1);
                }
            }
            if(ans < dp[i])ans=dp[i];
        }
        return ans;
    }
};
```

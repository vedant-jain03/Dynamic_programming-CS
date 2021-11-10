Problem Statement: https://leetcode.com/problems/jump-game-ii/

```
class Solution {
public:
    int jump(vector<int>& nums) {
        int n = nums.size();
        vector<int> dp(n,10000);
        dp[n-1] = 0;
        for(int i=n-2;i>=0;i--)
        {
            if(nums[i]!=0){
                for(int j=1;j<=nums[i];j++)
                {
                    if(i+j>=n)break;
                    dp[i] = min(dp[i],dp[i+j]+1);
                }
            }
        }
        return dp[0];
    }
};
```

Problem statement: https://leetcode.com/problems/burst-balloons/

```
class Solution {
public:
    int maxCoins(vector<int>& nums) {
        int n=nums.size();
        int dp[n][n];
        for(int g=0;g<n;g++)
        {
            for(int i=0, j=g;j<n;i++,j++)
            {
                int min=INT_MIN;
                for(int k=i;k<=j;k++)
                {
                    int left = (i==k)?0:dp[i][k-1];
                    int right = (j==k)?0:dp[k+1][j];
                    int val = ((i == 0)?1:nums[i-1])*nums[k]*((j==n-1)?1:nums[j+1]);
                    if(min < left+right+val)min=left+right+val;
                }
                dp[i][j]=min;
            }
        }
        return dp[0][n-1];
    }
};
```

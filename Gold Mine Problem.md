Problem Statement: https://www.geeksforgeeks.org/gold-mine-problem/

```
#include <bits/stdc++.h>
using namespace std;

int find(vector<vector<int>> gold)
{
    int m = gold.size();
    int n = gold[0].size();
    vector<vector<int>> dp(m,vector<int>(n,0));
    for(int i=0;i<m;i++)dp[i][n-1]=gold[i][n-1];
    
    for(int j=n-2;j>=0;j--)
    {
        for(int i=0;i<m;i++)
        {
            if(i==0){
                dp[i][j] = max(dp[i][j+1],dp[i+1][j+1])+gold[i][j];
            }
            else if(i==m-1){
                dp[i][j] = max(dp[i][j+1],dp[i-1][j+1])+gold[i][j];
            }
            else{
                dp[i][j] = max({dp[i][j+1],dp[i+1][j+1],dp[i-1][j+1]})+gold[i][j];
            }
        }
    }
    int ans = 0;
    for(int i=0;i<m;i++)ans = max(ans,dp[i][0]);
    return ans;
}

int main()
{
    vector<vector<int>> gold={
        {1, 3, 3},
        {2, 1, 4},
        {0, 6, 4}
    };
    cout<<find(gold);
}
```

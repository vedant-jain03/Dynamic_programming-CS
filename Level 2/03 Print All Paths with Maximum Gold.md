Problem Statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/goldmine-re-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

struct Pair {
    string psf;
    int i;
    int j;
};

void find(vector<vector<int>>& arr,int m,int n)
{
    vector<vector<int>> dp(m,vector<int>(n,0));
    for(int i=0;i<m;i++)dp[i][n-1] = arr[i][n-1];
    
    for(int j=n-2;j>=0;j--)
    {
        for(int i=0;i<m;i++)
        {
            if(i==0) {
                dp[i][j] = max(dp[i][j+1],dp[i+1][j+1])+arr[i][j];
            } 
            else if(i==m-1) {
                dp[i][j] = max(dp[i][j+1],dp[i-1][j+1])+arr[i][j];
            }
            else {
                dp[i][j] = max({dp[i][j+1],dp[i+1][j+1],dp[i-1][j+1]})+arr[i][j];
            }
        }
    }
    int ans = 0;
    for(int i=0;i<m;i++)ans = max(ans,dp[i][0]);
    cout<<ans<<"\n";
    queue<Pair> q;
    for(int i=0;i<m;i++)
    {
        if(dp[i][0] == ans)q.push({to_string(i)+"", i, 0});
    }
    
    while(!q.empty())
    {
        Pair best = q.front();
        q.pop();
        if(best.j == m-1) {
            cout<<best.psf<<"\n";
        }
        else if(best.i == 0) {
            int mx = max(dp[best.i][best.j+1],dp[best.i+1][best.j+1]);
            if(mx == dp[best.i][best.j+1]) {
                q.push({best.psf+" d2",best.i, best.j+1});
            }
            if(mx == dp[best.i+1][best.j+1]) {
                q.push({best.psf+" d3",best.i+1,best.j+1});
            }
        }
        else if(best.i == m-1) {
            int mx = max(dp[best.i][best.j+1],dp[best.i-1][best.j+1]);
            if(mx == dp[best.i][best.j+1]) {
                q.push({best.psf+" d2",best.i, best.j+1});
            }
            if(mx == dp[best.i-1][best.j+1]) {
                q.push({best.psf+" d1",best.i-1,best.j+1});
            }
        }
        else {
            int mx = max({dp[best.i][best.j+1],dp[best.i-1][best.j+1],dp[best.i+1][best.j+1]});
            if(mx == dp[best.i][best.j+1]) {
                q.push({best.psf+" d2",best.i, best.j+1});
            }
            if(mx == dp[best.i-1][best.j+1]) {
                q.push({best.psf+" d1",best.i-1,best.j+1});
            }
            if(mx == dp[best.i+1][best.j+1]) {
                q.push({best.psf+" d3",best.i+1,best.j+1});
            }
        }
    }
}

int main()
{
    int m;
    int n;
    cin>>m;
    cin>>n;
    vector<vector<int>> arr(m,vector<int>(n,0));
    for(int i=0;i<m;i++)
    {
        for(int j=0;j<n;j++)
        {
            cin>>arr[i][j];
        }
    }
    find(arr,m,n);
}
```

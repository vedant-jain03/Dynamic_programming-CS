Problem Statement: https://www.pepcoding.com/resources/online-java-foundation/recursion-backtracking/target-sum-subsets-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

struct Pair {
    int i;
    int j;
    string psf;
};

void find(int arr[],int sum,int n)
{
    vector<vector<bool>> dp(n+1,vector<bool>(sum+1,0));
    for(int i=0;i<=n;i++)dp[i][0] = true;
    for(int i=1;i<=sum;i++)dp[0][i] = false;
    
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=sum;j++)
        {
            if(j-arr[i-1]>=0) {
                dp[i][j] = dp[i-1][j-arr[i-1]] || dp[i-1][j];
            }
            else {
                dp[i][j] = dp[i-1][j];
            }
        }
    }
    cout<<dp[n][sum]<<"\n";
    
    // reverse engineering 
    queue<Pair> q;
    q.push({n,sum, ""});
    while(!q.empty())
    {
        Pair best = q.front();
        q.pop();
        int i = best.i;
        int j = best.j;
        if(i==0 && j==0){
            cout<<best.psf<<"."<<"\n";
            continue;
        }
        bool exc = dp[i-1][j];
        if(exc == true) {
            q.push({i-1,j,best.psf});
        }
        if(j-arr[i-1]>=0){
            bool inc = dp[i-1][j-arr[i-1]];
            if(inc == true) {
                q.push({i-1,j-arr[i-1],to_string(arr[i-1])+", "+best.psf});
            }
        }
    }
}

int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)cin>>arr[i];
    int sum;
    cin>>sum;
    find(arr,sum,n);
}
```

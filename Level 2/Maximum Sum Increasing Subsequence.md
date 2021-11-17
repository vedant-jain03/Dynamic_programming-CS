Problem Statement: https://www.geeksforgeeks.org/maximum-sum-increasing-subsequence-dp-14/

```
#include <bits/stdc++.h>
using namespace std;

int find(int arr[],int n)
{
    vector<int> dp(n);
    dp[0]=arr[0];
    int ans = arr[0];
    for(int i=1;i<n;i++)
    {
        dp[i] = arr[i];
        for(int j=0;j<i;j++)
        {
            if(arr[i]>=arr[j]) {
                dp[i] = max(dp[i], dp[j]+arr[i]);
            }
        }
    }
    for(auto x:dp)ans = max(ans,x);
    return ans;
}

int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)cin>>arr[i];
    cout<<find(arr,n);
}

```

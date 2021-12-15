Problem statement: https://www.geeksforgeeks.org/cutting-a-rod-dp-13/

# Method 1

```
#include <bits/stdc++.h>
using namespace std;

int find(int arr[],int n)
{
    int dp[n+1];
    dp[0]=0;
    for(int i=1;i<=n;i++)
    {
        int min=INT_MIN;
        for(int j=0;j<i;j++)
        {
            min = max(min, arr[j]+dp[i-j-1]);
        }
        cout<<min<<" ";
        dp[i]=min;
    }
    return dp[n];
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

# Method 2
```
#include <bits/stdc++.h>
using namespace std;

int find(int arr[],int n)
{
    int dp[n+1];
    dp[0]=0;
    dp[1]=1;
    for(int i=1;i<=n;i++)
    {
        int min=arr[i-1];
        int l=1;
        int r=i-1;
        while(l<=r)
        {
            min = max(min, dp[l]+dp[r]);
            l++;
            r--;
        }
        dp[i]=min;
    }
    return dp[n];
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

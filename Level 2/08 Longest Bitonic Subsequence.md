Problem Statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/lbs-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

int find(int n,int arr[])
{
    vector<int> inc(n,1);
    vector<int> dec(n,1);
    
    for(int i=1;i<n;i++)
    {
        for(int j=0;j<i;j++)
        {
            if(arr[i] >= arr[j]) {
                inc[i] = max(inc[i], inc[j]+1);
            }
        }
    }
    for(int i=n-2;i>=0;i--)
    {
        for(int j=n-1;j>i;j--) {
            if(arr[i] >= arr[j]) {
                dec[i] = max(dec[i], dec[i]+1);
            }
        }
    }
    int ans = 0;
    for(int i=0;i<n;i++)
    {
        ans = max(ans, inc[i]+dec[i]-1);
    }
    return ans;
}

int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)cin>>arr[i];
    cout<<find(n,arr);
}

```

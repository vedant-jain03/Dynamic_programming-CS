Problem Statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/min-jumps-re-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

struct Pair {
    int idx;
    string psf;
    int mjumps;
};

void printPath(vector<int>& dp,vector<int>& arr,int n)
{
    queue<Pair> q;
    Pair p1 = { 0, "0", dp[0]};
    q.push(p1);
    while(!q.empty())
    {
        Pair best = q.front();
        q.pop();
        if(best.mjumps == 0){
            cout<<best.psf<<" ."<<"\n";
            continue;
        }
        for(int i=1;i<=arr[best.idx];i++)
        {
            int ci = i+best.idx;
            if(ci<n && dp[ci] == best.mjumps-1)
            {
                string s1 = best.psf + " -> "+ to_string(ci);
                Pair p2 = {ci, s1, dp[ci]};
                q.push(p2);
            }
        }
    }
}

void find(vector<int>& arr,int n)
{
    vector<int> dp(n,10000);
    dp[n-1]=0;
    for(int i=n-2;i>=0;i--)
    {
        for(int j=1;j<=arr[i];j++)
        {
            if(i+j>=n)break;
            dp[i] = min(dp[i], dp[i+j]+1);
        }
    }
    cout<<dp[0]<<"\n";
    printPath(dp,arr,n);
}

int main()
{
    int n;
    cin>>n;
    vector<int> arr(n);
    for(int i=0;i<n;i++)cin>>arr[i];
    
    find(arr,n);
}
```

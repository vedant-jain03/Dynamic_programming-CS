Problem Statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/lis-re-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

struct Pair {
    int l;
    int i;
    int val;
    string psf;
};

void find(int arr[],int n)
{
    vector<int> dp(n,1);
    int ans = 1;
    int in = 0;
    for(int i=1;i<n;i++)
    {
        for(int j=0;j<i;j++)
        {
            if(arr[i] >= arr[j]) {
                dp[i] = max(dp[i], dp[j]+1);
            }
        }
        if(ans < dp[i]){
            ans = max(ans,dp[i]);
            in = i;
        }
    }
    cout<<ans<<"\n";
    
    queue<Pair> q;
    q.push({dp[in], in, arr[in], to_string(arr[in])+""});
    
    while(!q.empty()){
        Pair best = q.front();
        q.pop();
        if(best.l == 1) {
            cout<<best.psf<<"\n";
            continue;
        }
        for(int j=0;j<best.i;j++) {
            if(dp[j] == best.l-1 && arr[j]<=best.val) {
                q.push({dp[j],j,arr[j], to_string(arr[j])+" -> "+best.psf});
            }
        }
    }
}

int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++) cin>>arr[i];
    find(arr,n);
}
```

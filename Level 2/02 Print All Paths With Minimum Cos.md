Problem Statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/minimum-cost-path-re-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

struct Pair {
    int i;
    int j;
    string psf;
};

void bfs(vector<vector<int>>& dp,vector<vector<int>>& arr,int n)
{
    queue<Pair> q;
    Pair p1 = {n-1,n-1,""};
    q.push(p1);
    while(!q.empty()){
        Pair best = q.front();
        q.pop();
        if(best.i ==0 && best.j==0){
            string s1 = best.psf;
            reverse(s1.begin(),s1.end());
            cout<<s1<<"\n";
            continue;
        }
        else if(best.i == 0) {
            Pair x = {best.i, best.j-1, best.psf+"H"};
            q.push(x);
        }
        else if(best.j == 0) {
            Pair y = {best.i-1 , best.j, best.psf+"V"};
            q.push(y);
        }
        else {
            
            if(dp[best.i][best.j-1] == dp[best.i-1][best.j]){
                Pair x = {best.i,best.j-1,best.psf+"H"};
                Pair y = {best.i-1,best.j,best.psf+"V"};
                q.push(x);
                q.push(y);
            }
            else if(dp[best.i][best.j-1] > dp[best.i-1][best.j]){
                Pair y = {best.i-1,best.j,best.psf+"V"};
                q.push(y);
            }
            else {
                Pair x = {best.i,best.j-1,best.psf+"H"};
                q.push(x);
            }
        }
    }
}

void find(vector<vector<int>>& arr,int n)
{
    vector<vector<int>> dp(n,vector<int>(n,0));
    dp[0][0]=arr[0][0];
    for(int i=1;i<n;i++){
        dp[i][0] = dp[i-1][0]+arr[i][0];
        dp[0][i] = dp[0][i-1]+arr[0][i];
    }
    
    for(int i=1;i<n;i++)
    {
        for(int j=1;j<n;j++)
        {
            dp[i][j] = min(dp[i-1][j],dp[i][j-1])+arr[i][j];
        }
    }
    bfs(dp,arr,n);
}

int main()
{
    int n;
    cin>>n;
    vector<vector<int>> arr(n,vector<int>(n));
    for(int i=0;i<n;i++)
    {
        for(int j=0;j<n;j++)
        {
            cin>>arr[i][j];
        }
    }
    find(arr,n);
}


```

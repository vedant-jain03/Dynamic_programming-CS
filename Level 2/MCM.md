Problem statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/matrix-chain-multiplication-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

int MatrixChainOrder(int arr[],int n)
{
    vector<vector<int>> dp(n-1, vector<int> (n-1));
    
    for(int g=0;g<dp.size();g++)
    {
        for(int i=0, j=g; j<dp.size();i++,j++)
        {
            if(g==0) {
                dp[i][j] = 0;
            }
            else if(g==1) {
                dp[i][j] = arr[i] * arr[j] * arr[j+1];
            }
            else {
                int min = INT_MAX;
                for(int k=i;k<j;k++)
                {
                    int lc = dp[i][k];
                    int rc = dp[k+1][j];
                    int mc = arr[i] * arr[k+1] * arr[j+1];
                    int tc = lc+rc+mc;
                    if(tc < min) min = tc;
                }
                dp[i][j] = min;
            }
        }
    } 
    return dp[0][dp.size()-1];
}

int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)cin>>arr[i];
    cout<<MatrixChainOrder(arr,n);
}
```

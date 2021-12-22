Problem statement: https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/dynamic-programming/lpss-official/ojquestion

```
#include <bits/stdc++.h>
using namespace std;

int find(string s)
{
    int n=s.size();
    bool dp[n][n];
    int ans=INT_MIN;
    for(int g=0;g<n;g++)
    {
        for(int i=0,j=g;j<n;i++,j++)
        {
            if(g==0) dp[i][j]=true;
            else if(g==1)
            {
                dp[i][j]=(s[i]==s[j]);
            }
            else {
                if(s[i]==s[j] && dp[i+1][j-1])dp[i][j]=true;
                else dp[i][j]=false;
            }
            if(dp[i][j]==true && g>ans){
                ans=g;
            }
        }
    }
    return ans+1;
}

int main()
{
    string s;
    cin>>s;
    cout<<find(s);
}
```

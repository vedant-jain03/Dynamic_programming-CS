# Dynamic Programming

Dynamic Programming used to solve a particular question using it's past reference.
It is used when thier are two cases :
- Overlapping Subproblem (Ex: Fib[5] = Fib[4]+Fib[3] and Fib [3] is subproblem for fib[4] and fib[5] which can be computed and store to solve it)
- Optimal Substructure (Ex: Recurence Tree)

### Two Types of Approaches:
- Top-Down Approach: Where we solve from higher possible value (ex: fib[n]) to lower possible value(fib[2]).

  Top Down Approach where memoization + recusrion is used, memoization means to store the values in hashmap or vector.

- Bottom-up Approach: Where we solve from lowest possible value to higher (n);
ex: dp[n] = dp[n-1]+dp[n-2]

## Fibonacci:
### Recursion
TC: O(2^n)
SC: O(n)[Call Stack]
```
#include <bits/stdc++.h>
using namespace std;

int fib(int n)
{
    if(n==0 || n==1)return n;
    int ans = fib(n-1)+fib(n-2);
    return ans;
}
int main()
{
    int n;
    cin>>n;
    cout<<fib(n);
}
```

### Top-down Dp(Recursion + Memoization)
TC: O(n)
SC: O(n)[Extra Array]
```
#include <bits/stdc++.h>
using namespace std;

int fib(int n,int dp[])
{
    if(n==0 || n==1)return n;
    if(dp[n]!=0)return dp[n];
    int ans = fib(n-1,dp)+fib(n-2,dp);
    return dp[n] = ans;
}
int main()
{
    int n;
    cin>>n;
    int dp[100]={0};
    cout<<fib(n,dp);
}
```

### Bottom-up(Iterative Solution)
TC: O(n)
SC: O(n)
```
#include <bits/stdc++.h>
using namespace std;

int fib(int n)
{
    vector<int> dp(n+1,0);
    dp[0]=0;
    dp[1]=1;
    for(int i=2;i<=n;i++)
    {
        dp[i] = dp[i-1]+dp[i-2];
    }
    return dp[n];
}
int main()
{
    int n;
    cin>>n;
    cout<<fib(n);
}
```

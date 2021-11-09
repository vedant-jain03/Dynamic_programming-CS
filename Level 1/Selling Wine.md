# Selling Wine

Problem statement:

Given n wines in a row, with integers denoting the cost of each wine respectively. Each year you can sell the first or the last wine in the row. Let the initial profits from the wines be P1, P2, P3…Pn. In the Yth year, the profit from the ith wine will be Y*P[i]. The goal is to calculate the maximum profit that can be earned by selling all the wines.

example:

price: [2 4 6 2 5];

Suppose Using Greedy (Locally Optimised) We will try to find min price between last and first;

2(1) + 4(2) + 5(3) + 2(4) + 6(2) = 63 rs.

Using DP or checking every case:

2(1) + 5(2) + 2(3) + 4(4) + 6(5) = 64 rs.

- Recurrence Relation

  `f(left,right,year) = max( price[first] * year + f(left+1,right,year+1) , price[last] * year + f(left,right-1,year+1) );`

## Top-Down with Memoization
```
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> dp(100,vector<int>(100,-1));

int util(vector<int>& price,int i,int j,int year)
{
    if(i>j)return 0;
    if(i==j)return price[i]*year;
    if(dp[i][j]!=-1)return dp[i][j];
    int left = price[i]*year + util(price,i+1,j,year+1);
    int right = price[j]*year + util(price,i,j-1,year+1);
    return dp[i][j] = max(left,right);
}

int maxprice(vector<int> price,int n)
{
    return util(price,0,n-1,1);
}

int main()
{
    vector<int> price = {2,4,6,2,5};
    cout<<maxprice(price,price.size());
}
```

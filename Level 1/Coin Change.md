# Coin Change

Given a value N, if we want to make change for N cents, and we have infinite supply of each of S = { S1, S2, .. , Sm} valued coins, how many ways can we make the change? The order of coins doesn’t matter.
For example, for N = 4 and S = {1,2,3}, there are four solutions: {1,1,1,1},{1,1,2},{2,2},{1,3}. So output should be 4. For N = 10 and S = {2, 5, 3, 6}, there are five solutions: {2,2,2,2,2}, {2,2,3,3}, {2,2,6}, {2,3,5} and {5,5}. So the output should be 5.

Approach: We will try to find in two condition
- if we have consider ith coin then next target to find is ways to make sum-arr[i] considering ith coin again
- if we have not consider then next target to find is ways to make sum with not considering ith coin further more

` f(sum,n,arr) = f(sum-arr[n-1],n,arr) + f(sum,n-1,arr) `



### Recursive

```
#include <bits/stdc++.h>
using namespace std;

int findways(int arr[],int sum,int n)
{
    if(sum<0)return 0;
    if(sum == 0)return 1;
    if(n<=0 && sum>0)return 0;
    return findways(arr, sum, n-1)+findways(arr,sum-arr[n-1],n);
}
int main()
{
    int sum = 4;
    int arr[] = {1,2,3};
    int n=sizeof(arr)/sizeof(arr[0]);
    cout<<findways(arr,sum,n);
}
```

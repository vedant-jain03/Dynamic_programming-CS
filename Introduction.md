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


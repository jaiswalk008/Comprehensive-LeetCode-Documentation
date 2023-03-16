# [Climbing Stairs](https://leetcode.com/problems/climbing-stairs)

### Intuition:
- This is classical DP problem similar to Fibonacci numbers.I will be using a Bottom-up approach starting with the base cases and then build up the solution iteratively by solving smaller subproblems and storing their solutions in a table or array.
- If we observe the number of ways to reach the stair n equals the number of ways to reach the stair n-1 plus the number of ways to reach to stair n-2.
- This is because a person can either climb one stair from n-1 stairs or two stairs from n-2 stairs to reach the nth stair.
- For example, if n=3 --> possible cases : [ (1,1,1) , (1,2) , (2,1) ] total 3 cases which are :
    1. from stair 3, we go 1 down to stair 2, then 1 down stair 1 and then 1 down to the bottom.
    2. from stair 3, we go 1 down to stair 2 and then 2 down to the bottom.
    3. from stair 3, we go 2 down to stair 1 and 1 down to the bottom.

```
dp[1] = 1
dp[2] = 2
dp[3] = dp[2] + dp[1] = 2 + 1 = 3
dp[4] = dp[3] + dp[2] = 3 + 2 = 5
dp[5] = dp[4] + dp[3] = 5 + 3 = 8
      dp[5]
     /     \
  dp[4]     dp[3]
  /   \     /   \
dp[3] dp[2] dp[2] dp[1]
 / \
dp[2] dp[1]
```
### Approach:
We can use an array dp to store the number of distinct ways to climb i stairs. \
Initially, dp[1] and dp[2] are set to 1 and 2, respectively, as there is only one way to climb one stair and two ways to climb two stairs.\
Then, we use a loop to fill the dp array from dp[3] to dp[n], using the recurrence relation dp[i] = dp[i-1] + dp[i-2].\
By the end of the loop, dp[n] will contain the number of distinct ways to climb n stairs, and we can return this value as the solution to the problem.\
**Code:**
```
class Solution {
public:
    int climbStairs(int n) {
        int dp[46];
        dp[1]=1;
        dp[2]=2;
        for(int i=3;i<=n;i++) dp[i]=dp[i-1]+dp[i-2]; 
        return dp[n];
    }
};
```

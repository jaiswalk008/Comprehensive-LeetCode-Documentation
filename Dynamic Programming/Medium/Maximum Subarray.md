# [Maximum Subarray](https://leetcode.com/problems/maximum-subarray)
### INtuition:
The intuition behind this algorithm is to recognize that if we have a subarray with a negative sum and we add any element to it then which is more bigger the new sum or that element itself . 
If the element is bigger, we can discard the subarray and start a new subarray at the current element.\
By keeping track of the maximum sum seen so far, we can ensure that we always return the maximum subarray sum.

### Approach:
 - At each iteration, we update the value of sum by taking the maximum of the sum plus the current element (sum+nums[i]) and the current element (nums[i]). 
 - We also update the value of maxSum by taking the maximum of the current maxSum and the updated value of sum. 
 - By the end of the loop, we have computed the maximum subarray sum, which we return as the output.
 
 **Example** : Input: [-2, 1, -3, 4, -1, 2, 1, -5, 4]
 Sure, let's consider the input array nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4] as an example to illustrate the Kadane's algorithm for finding the maximum subarray sum.

Step 1: Initialize variables

We start by initializing two variables "maxSum" and "sum" to the first element of the array, which is -2 in this case.
maxSum = -2 and sum = -2.
Step 2: Iterate through the array

We iterate through the array starting from the second element.
At each index i, we update the "sum" and "maxSum" variables using the Kadane's algorithm.
For index i = 1:

sum = max(-2 + 1, 1) = 1.
maxSum = max(-2, 1) = 1.
For index i = 2:

sum = max(1 - 3, -3) = -2.
maxSum = max(1, -2) = 1.
For index i = 3:

sum = max(-2 + 4, 4) = 4.
maxSum = max(1, 4) = 4.
For index i = 4:

sum = max(4 - 1, -1) = 3.
maxSum = max(4, 3) = 4.
For index i = 5:

sum = max(3 + 2, 2) = 5.
maxSum = max(4, 5) = 5.
For index i = 6:

sum = max(5 + 1, 1) = 6.
maxSum = max(5, 6) = 6.
For index i = 7:

sum = max(6 - 5, -5) = 1.
maxSum = max(6, 1) = 6.
For index i =
 
**Code:**
```
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxSum=nums[0],sum=nums[0];   
        for(int i=1;i<nums.size();i++){
            sum = max(sum+nums[i],nums[i]);
            maxSum = max(maxSum,sum);
        }
        return maxSum;
    }
};
```

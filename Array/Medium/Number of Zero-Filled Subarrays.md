# [Number of Zero-Filled Subarrays](https://leetcode.com/problems/number-of-zero-filled-subarrays/)

### Intuition:
  For nth continuous 0 encountered, the number of subarray that can be generated by it is n.
### Approach:
- The approach used in this function is to iterate through the nums vector and maintain two variables: ct (count of zero-filled subarrays) and curr (current length of the contiguous zero-filled subarray). 
- Whenever a zero is encountered, the curr variable is incremented and added to the ct variable.
- If a non-zero number is encountered, the curr variable is reset to zero.

Example: [0,0,0,0]
  - for 0 at index-0: 1 =1
  - for 0 at index-1: 1(subarray of size 1) + 1(subarray of size 2) =2
  - for 0 at index-2: 1(subarray of size 1) +1(subarray of size 2) + 1(subarray of size 3) =3
  - for 0 at index-3: 1(subarray of size 1) +1(subarray of size 2) + 1(subarray of size 3) + 1(subarray of size 4) =4

**Code:**
```
class Solution {
public:
    long long zeroFilledSubarray(vector<int>& nums) {
        long long ct= 0;
        int curr= 0;
        for(int n: nums){
            if(n==0) ct+=(++curr);
            else curr=0;
        }
        return ct;
    }
};
```
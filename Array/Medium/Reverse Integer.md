# [Reverse Integer](https://leetcode.com/problems/reverse-integer)

### Approach: This is a simple problem of reversing the digits of a number with the condition of checking the overflow of number.
### Time Complexity : O(logN)
### Overflow condition : 
Range of _int_ data type :  -2147483648 to 2147483647.

if (res > INT_MAX / 10 || (res == INT_MAX / 10 && temp > 7)) return 0;

In (res == INT_MAX / 10 && temp > 7) ==> INT_MAX/10 + (temp>7) will cause an overflow.\
e.g., INT_MAX/10 = 2147483647 and temp=8 so thats 2147483648 >2147483647


**Code:**
#
```
class Solution {
public:
    int reverse(int x) {
        int sign = x>0?1:-1;
        x = abs(x);
        int res = 0;
        while (x > 0) {
            int temp = x % 10;
            if (res > INT_MAX / 10 || (res == INT_MAX / 10 && temp > 7)) return 0;
            res = res * 10 + temp;
            x /= 10;
        }
        return sign * res;
    }
};
```

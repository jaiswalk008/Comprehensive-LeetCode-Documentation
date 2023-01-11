# [First Bad Version](https://leetcode.com/problems/first-bad-version/)

<pre>
class Solution {
public:
    int firstBadVersion(int n) {
        int low = 1;
        int high = n;
        int mid;
        while(low < high){
            mid = low + (high-low)/2;
            if(isBadVersion(mid)){
                high= mid;
            }
            else low = mid+1; 
        }
        return high;
    }
};
</pre>

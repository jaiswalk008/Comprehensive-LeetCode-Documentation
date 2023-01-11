# [Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)

<pre>
class Solution {
public:
    int findKthPositive(vector<int>& arr, int k) {
        int low = 0;
        int high = arr.size()-1;
        int mid;
        while(low<=high){
            mid = low + (high -low)/2;
            if((arr[mid]-mid-1)>=k) high = mid-1;
            else low = mid+1;
        }
        return low+k;
    }
};
</pre>

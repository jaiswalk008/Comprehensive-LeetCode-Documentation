# [Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

<pre>
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int ans=0,low=0,high = nums.size()-1,mid;
        if(high==0) return nums[0];
        else if(nums[0] < nums[1]) return  nums[0];
        else if(nums[high ] > nums[high-1]) return nums[high];
        else{
            while(low <= high){
                mid = low + (high-low)/2;
                if( nums[mid] > nums[mid-1] && nums[mid] < nums[mid+1]) {
                    return nums[mid];
                }
                else if(mid%2==0) {
                    if(nums[mid-1]==nums[mid]) high=mid;
                    else low= mid;
                }
                else{
                    if(nums[mid-1]==nums[mid]) low=mid;
                    else high = mid;
                }
            }
        }    
        return ans;
    }
};
</pre>

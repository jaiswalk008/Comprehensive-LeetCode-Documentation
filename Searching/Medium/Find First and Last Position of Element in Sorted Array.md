# [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

<pre>
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int low= 0, high= nums.size()-1,mid,new_low;
        vector <int> ans(2,-1);
        bool flag= false;
        while(low<=high){
            mid = low + (high - low)/2;
            if(nums[mid]==target ) {
                if(!flag){
                    new_low = mid;
                    flag = true;
                }
                high = mid-1;
            }
            else if(nums[mid] < target) low = mid+1;
            else high = mid-1;
        }
        if(flag ) ans[0]=high +1;
        
        high = nums.size()-1;
        while(new_low<=high){
            mid = new_low + (high - new_low)/2;
            if(nums[mid]==target ) {
                new_low = mid+1;
            }
            else high = mid-1;
        }
        
        if(flag) ans[1]= new_low-1;
        return ans;
    }
};
</pre>

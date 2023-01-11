# [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

<pre> 
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int low= 0;
        int high = nums.size()-1;
        int mid ;
        while(low<=high){
            mid = (low+high)/2;
     
            if(nums[mid]==target) return mid;
            else if(nums[low]<=nums[mid]){
                if(nums[low]<=target && target<=nums[mid]) high = mid-1;
                else low = mid+1;
            }
            else{
                if(target<=nums[high] && target >= nums[mid]) low = mid+1;
                else high = mid-1;
            }
        }
        return -1;
    }
};
</pre>

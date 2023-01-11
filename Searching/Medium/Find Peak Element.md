# [Find Peak Element](https://leetcode.com/problems/find-peak-element/)

<pre>
class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        int low  =0;
        int high = nums.size()-1;
        int mid; //
        if(high==0) return 0;
        if(nums[0] > nums[1]) return 0;
        if(nums[nums.size()-1] > nums[nums.size()-2]) return (nums.size()-1);
        while(low <= high){
            mid = ((unsigned int)low + (unsigned int)high) >> 1;
            
            if(high==1) return high;
            if(mid!=0 && mid!=nums.size()-1){
                if(nums[mid] > nums[mid-1] && nums[mid]>nums[mid+1]){
                    return mid;
                }
                else if(nums[mid+1] > nums[mid]) low = mid+1;
                else high = mid-1; 
            }
        }
        return mid;
    }
};
</pre>

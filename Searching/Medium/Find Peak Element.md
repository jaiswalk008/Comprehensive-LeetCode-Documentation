# [Find Peak Element](https://leetcode.com/problems/find-peak-element/)
#### Intuition : An important idea for solving this problem comes from the constraint: **_nums[i] != nums[i + 1] for all valid i_**
which means the next element will either be greater or less than the current element.

#### Idea: We need to do this in O(logn), so we will use a modified form of Binary search.

### Approach : 
Now, after calculating _mid_, there can only be **three** possible cases:
 1. If _mid_ is the peak value, then we will return it.
 2. If the _mid_ value is less than the element before it, there will be a _peak_ element in the _left_ subarray.
	Note: There can be a peak element in the _right_ subarray but it is not guaranteed. e.g., arr[]= 4,6,3,2,1
 3. If the _mid_ value is greater than the element before it, there will be a _peak_ element in the _right_ subarray.
 
 ### Some base cases : 
   The array could be strictly increasing or strictly decreasing and as we have to return any of the possible peaks, so we could    add a condition to check whether the 1st element/last element could be the peak or there can be only one element in the          array.
 ### Input  : 1,2,1,3,6,5,4
 _low_ = 0 , _high_ = 6 , _mid_ = 3\
 --> arr[mid] = 3 and arr[mid] > arr[mid-1] (**case 3**), so we will increment _low_\
 _low_ = 4 , _high_ = 6 , _mid_ = 5\
 --> arr[mid] = 5 which is less than the element before it(**case 2**), so we will decrement _high_\
 _low_ = 4 , _high_ = 4 , _mid_ = 4\
 --> arr[mid] = 6 which is the peak element, so we will return its index.
   
<pre>
class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        
        int low= 1,high = nums.size()-2;
        // if the array size = 1
        if(nums.size()==1) return 0;
        // if the first element is a peak element
        else if(nums[0]>nums[1]) return 0;
        // if the last element is a peak element
        else if(nums[high]< nums[high+1]) return high+1;
        else{
            while(low<=high){
                int mid  = low + (high-low)/2;
                if(nums[mid]>nums[mid-1] && nums[mid] > nums[mid+1]) return mid;
                else if(nums[mid+1]>nums[mid]) low = mid+1;
                else high = mid-1;   
            }
        }
        return -1;
    }
};
</pre>

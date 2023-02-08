# [Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

#### Intuition : In this problem, every element except one will have exactly one duplicate, so that means the size of the array will be an odd number. Therefore, if we divide the array in two halves, one will be of even size and the other will be of odd size, and we will continue to divide the array with the odd size because the single element will be in the subarray with odd size
_ Note: here we will take even sized array as we are using zero based index._
#### Idea : As the problem needs to be solved in O(logn), so we have to use the methodology of Binary Search.

### Approach :

Now, we need to calculate _mid_, there can only be **three** possible cases after that:\
1._mid_ is the index of the single element and hence we will return it.\
2. 
<pre>
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int low=0,high = nums.size()-1,mid;
        //if there is only one element
        if(high==0) return nums[0];
        //some edge cases for getting results faster
        else if(nums[0] < nums[1]) return  nums[0];
        else if(nums[high] > nums[high-1]) return nums[high];
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
        //can return anything as there will always be an answer returned from the above if..else condition
        return mid;
    }
};
</pre>

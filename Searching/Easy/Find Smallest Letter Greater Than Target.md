# [Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

#### idea: Whenever the input is in sorted order, chances are higher that we need to use Binary Search.


***We should use mid = low + (high-low)/2 instead of mid = (low+high)/2 because the latter can result in integer overflow.***

**Example:** low = 1170105034 \
high = 1347855270 \
(low + high) / 2 //outputs  -888503496 \
low + (high - low) / 2 //outputs 1258980152 

##### Logic: Here we will use a modified Binary search algorithm and keep searching until the **_low_** bound becomes larger than the **_upper_** bound. Check for the edge case.
##### Since we need to return the element greater than the target so if the element is greater than or equal to the target we will increment **_low_** otherwise decrement **_high_**. This works even if the target is not present in the array because it narrows down the search for the element just bigger than the target. And will finally, return the element low is pointing to.
  

<pre>
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        int low = 0, high = letters.size()-1, mid;
        
        //Edge Case : checking if the target is in the array or not.
        
        if(target<letters[0] || target>=letters[high]) return letters[0];
        while(low<=high){
            mid = low + (high-low)/2;
            if(target>=letters[2]) low = mid+1;
            else high = mid-1;
        }
        return letters[low];
    }
};
</pre>

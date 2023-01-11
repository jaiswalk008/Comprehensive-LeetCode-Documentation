# [Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/description/)

<pre>
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int low = 0 , high = arr.size()-1, mid;
        while(low<=high){
            mid = low + (high - low)/2;
          
            if(mid!=0 && mid!=arr.size()-1){
               
                if(arr[mid] > arr[mid-1] && arr[mid] > arr[mid+1]) {
                   
                    return mid;
                }
                else if(arr[mid] > arr[mid-1] && arr[mid] < arr[mid+1]) low= mid+1;
                else high = mid-1;
               
            }
            else if(mid==0) low++;
            else high--;   
        }
        return mid;
    }
};
</pre>

# [Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

<pre>
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        int low = 0;
        int high = letters.size()-1;
        int mid;
        if(target<letters[0] || target>=letters[high]) return letters[0];
        while(low<=high){
            mid = low + (high-low)/2;
            if(target>=letters[mid]) low = mid+1;
            else high = mid-1;
        }
        return letters[low];
    }
};
</pre>

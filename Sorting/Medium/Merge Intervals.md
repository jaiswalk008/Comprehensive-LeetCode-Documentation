  # [Merge Intervals](https://leetcode.com/problems/merge-intervals/)
  
  ### Intuition:
  There can only be two cases:
  Case 1. The start of the current interval lies in the last interval present in the result.
  Case 2. The start of the current interval is greater than the last interval.
  
  Example : [[1,3],[2,6],[5,8],[8,8],[11,12]]
 - First we will add the first vector([1,3]) into the result.
 - Now i=1, 2 is between [1,3] (case 1) and the second part will max(3,6) = 6 --> res = [[1,6]]
 - i=2, 5 is between [1,6] (case 1) and the second part will max(6,8) = 8 --> res = [[1,8]]
 - i=3, 8 is between [1,8] (case 1) and the second part will max(8,8) = 8 --> res = [[1,8]]
 - i=4, 11 is greater than 8 so res = [[1,8],[11,12]]
 
  **Code:**
```
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(intervals.begin(),intervals.end());
        vector<vector<int>> ans;
        ans.push_back(intervals[0]);
        for(int i=1;i<intervals.size();i++){
            int last = ans.size()-1;
            if(intervals[i][0]>ans[last][1]) ans.push_back(intervals[i]);
            else ans[last][1] = max(ans[last][1] , intervals[i][1]);
        }
        return ans;
    }
};
```

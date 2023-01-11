# [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

<pre>
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int low =0;
        int high = numbers.size()-1;
      
        int s=0;
        vector<int> ans;
        while(low < high){
            s= numbers[low] + numbers[high];
            if(s==target){
                ans.push_back(low+1);
                ans.push_back(high+1);
                break;
            }
            else if(s < target) low++;
            else high--;
        }   
        return ans;
    }
};
</pre>

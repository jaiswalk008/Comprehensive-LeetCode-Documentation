# [Combination Sum](https://leetcode.com/problems/combination-sum/)

**Code:**
```
class Solution {
public:
    static void findCombination(int ind ,int sum, vector<int>& candidates,vector<int> &temp, vector<vector<int>> &res, int target){
        if(sum==target){
            res.push_back(temp);
            return;
        }
        else if(candidates.size()==ind) return;
        else if(sum>target) return ;
        else{
            temp.push_back(candidates[ind]);
            findCombination(ind,sum+candidates[ind],candidates ,temp, res,target);
            temp.pop_back();
            findCombination(ind+1,sum,candidates ,temp, res,target);
        }
    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> res;
        vector<int> temp;
        findCombination(0,0,candidates ,temp, res,target);
        return res;
    }
};
```

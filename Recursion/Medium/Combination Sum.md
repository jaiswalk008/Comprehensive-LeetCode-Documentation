# [Combination Sum](https://leetcode.com/problems/combination-sum/)

### Approach:
- The approach used in this solution is recursive backtracking.
- In the recursive case, we have two options: we can either include the current element at the current index, or we can exclude it.
- If we exclude it, we simply call the function recursively with the next element, and the temporary vector remains unchanged.
- If we include it, we add the current element to the temporary vector and to variable sum, call the function recursively with the same index, and the temporary vector updated.
- After the recursive call, we remove the current element from the temporary vector to restore it to its original state and also the variable sum.


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
            //including the element and calling the function with the same index
            temp.push_back(candidates[ind]);
            findCombination(ind,sum+candidates[ind],candidates ,temp, res,target);
            //removing the element
            temp.pop_back();
            //excluding the element and calling the function with the next index
            findCombination(ind+1,sum,candidates ,temp, res,target);
        }
    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        //res for storing the result
        vector<vector<int>> res;
        vector<int> temp;
        findCombination(0,0,candidates ,temp, res,target);
        return res;
    }
};
```

# [Subsets](https://leetcode.com/problems/subsets)
### Approach:
- The approach used in this solution is recursive backtracking.
- In the recursive case, we have two options: we can either include the current element at the current index, or we can exclude it. 
- If we exclude it, we simply call the allSets function recursively with the next element, and the temporary vector remains unchanged. 
- If we include it, we add the current element to the temporary vector, call the allSets function recursively with the index incremented by one, and the temporary vector updated.
- After the recursive call, we remove the current element from the temporary vector to restore it to its original state.(As we have to keep using that particular vector)

**Time Complexity** : O(2^n)
```
Recursion Tree :
                          []
                /                   \
              /                       \
          [1]                           []
        /     \                      /      \
     [1,2]     [1]                  [2]      []
      /   \    /  \                /  \      / \
[1,2,3] [1,2][1,3][1]        [2,3]     [2]  [3] []

The tree starts with an empty subset, represented as an empty vector.
At each level of the tree, we add the next element of the input vector to the subset, or we don't add it. 
The branches of the tree represent the different choices we can make, and the nodes represent the different subsets we can generate. 
```
**Code:**
 ```
 class Solution {
public:
    static void allSets(int index,vector<int>& nums ,vector<vector<int>> &res,vector<int>& temp){
        
        if(index==nums.size()){
            res.push_back(temp);
            return;
        }
        //not taking the element
        allSets(index+1,nums,res,temp);
        
        //taking the element
        
        temp.push_back(nums[index]);
        allSets(index+1,nums,res,temp);
        temp.pop_back();
    }
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> res;
        vector<int> temp;
        allSets(0,nums,res,temp ) ;
        return res;
    }
};
```

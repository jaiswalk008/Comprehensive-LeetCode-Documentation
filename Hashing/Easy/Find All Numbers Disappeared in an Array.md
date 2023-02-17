# [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)

### C++ code:

<pre>
// 4 3 2 7 8 2 3 1  
// 7 3 2 4 8 2 3 1
// 3 3 2 4 8 2 7 1
// 2 3 3 4 8 2 7 1
// 3 2 3 4 8 2 7 1
// 3 2 3 4 1 2 7 8
// 1 2 3 4 3 2 7 8
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        int i=0;

        while(i < nums.size()){
            if(nums[i] == nums[nums[i]-1]) i++;
            else{
                int temp = nums[nums[i]-1];
        
                nums[nums[i]-1] = nums[i];
                nums[i]=temp;
            }
        }
        vector<int> ans;
        for(int iter=0;iter < nums.size();iter++){
        
            if(nums[iter]!=(iter+1)) ans.push_back(iter+1);
        }
        return ans;
    }
};
</pre>

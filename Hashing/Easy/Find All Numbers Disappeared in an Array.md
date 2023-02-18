# [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)

### Idea : bringing the correct element at the correct position by swapping and then checking if an element is at the right _index_ or not.
#### input array :  4 3 2 7 8 2 3 1  
when _i=0_ :\
    _As 1 has to be at index 1, so we will replace 4 with arr[4] , then will keep swapping till 1 comes at index 1_\
   4 3 2 7 8 2 3 1  &rarr; 7 3 2 4 8 2 3 1 &rarr; 3 3 2 4 8 2 7 1 &rarr;  2 3 3 4 8 2 7 1 &rarr; 3 2 3 4 8 2 7 1 &rarr; &rarr; 3 2 3 4 1 2 7 8 &rarr; 1 2 3 4 3 2 7 8\
Now _i=1_:\
    _now 2 is already at the correct index so i will be incremented and goes on like this_\
**Now in the second for loop we will check which index doesnot have its correct element**
    
### C++ code:

<pre>

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

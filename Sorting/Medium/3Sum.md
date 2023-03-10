# [3Sum](https://leetcode.com/problems/3sum/)
### Prerequisite : [Two-pointers Technique](https://www.geeksforgeeks.org/two-pointers-technique/)
### Required Time Complexity : O(N^2)
### Required Space Complexity : O(1)
### Intuition
We have to first sort the input array and then use the two-pointer technique,
where two pointers are used to traverse the sorted vector from both ends 
while maintaining a third pointer for the current element. 

**Note:**  We need to use two while loops for skipping duplicates
**Code:**
#
```
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> res;
        sort(nums.begin(),nums.end());
        for(int k=0;k<nums.size()-2;k++){
            // skip duplicates
            if (k > 0 && nums[k] == nums[k-1]) continue;
            
            int i=k+1,j=nums.size()-1;
            while(i<j){

                if((nums[i] + nums[j] + nums[k])==0){
                    vector<int> temp = {nums[k], nums[i], nums[j]};
                    res.push_back(temp);

                    // skip duplicates
                    while (i < j && nums[i] == nums[i+1]) i++;
                    while (i < j && nums[j] == nums[j-1]) j--;
                    
                    i++;
                    j--;
                }
                else if((nums[i] + nums[j])<abs(nums[k])) i++;
                else j--;
            }
        }
        return res;
    }
};
```
**Java Code:**
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        
        // sort the input array
        Arrays.sort(nums);
        
        // iterate over the array, fixing the first element of the triplet
        for (int k = 0; k < nums.length - 2; k++) {
            // skip duplicates
            if (k > 0 && nums[k] == nums[k-1]) {
                continue;
            }
            
            // set pointers for the remaining elements
            int i = k + 1;
            int j = nums.length - 1;
            
            // iterate over the remaining elements
            while (i < j) {
                int sum = nums[k] + nums[i] + nums[j];
                
                // if the sum is zero, add the triplet to the result list
                if (sum == 0) {
                    res.add(Arrays.asList(nums[k], nums[i], nums[j]));
                    
                    // skip duplicates
                    while (i < j && nums[i] == nums[i+1]) {
                        i++;
                    }
                    while (i < j && nums[j] == nums[j-1]) {
                        j--;
                    }
                    
                    i++;
                    j--;
                }
                // if the sum is less than zero, increment the left pointer
                else if (sum < 0) {
                    i++;
                }
                // if the sum is greater than zero, decrement the right pointer
                else {
                    j--;
                }
            }
        }
        
        return res;
    }
}
```

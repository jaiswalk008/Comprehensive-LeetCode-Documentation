  # [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)
  
  ### Intuition:
The intuition behind this approach is that by placing each positive integer at its correct position, we can easily identify the missing positive integer. By swapping each element with the element at its correct index, we can ensure that all positive integers from 1 to n are present in the array and are in their correct positions.

### Approach:
- The approach used in this problem is to use an in-place swapping algorithm to move each positive integer to its correct position.
- We traverse the nums vector using a while loop, and for each index i, we check if the current number at nums[i] is a positive integer between 1 and n.
- If so, we check if the number is already at its correct position by checking the value at the index nums[i]-1 in the array.
- If not, we swap the current number with the number at the index nums[i]-1.
- Next, we traverse the updated nums vector again using a for loop to find the first missing positive integer. If at any index i, i+1 does not match the value at nums[i], we know that i+1 is the smallest missing positive integer. 

**Test Case**: arr= [3,4,-1,1]
- i=0, nums[0]= 3 and it will be swapped with element at index = 2(3-1)
  --> arr = [-1,4,3,1]
- i=0, nums[0]= -1 as nums[i]<0 so i++
- i=1, nums[1]= 4 and it will be swapped with element at index = 3
  --> arr= [-1,1,3,4]
- i=1, nums[1] 1 and it will be swapped with element at index = 0
  --> arr = [1,-1,3,4]
- i=1, nums[1]= -1 as nums[i]<0 so i++
- i=2, nums[2] and nums[nums[2]-1] are equal so i++.
- i=3, nums[3] and nums[nums[3]-1].

Now in the second loop --> at index 1(2-1) , 2 is not present so 2 will be the answer.

 **Code:**
 ```
 class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int i=0;
        while(i < nums.size()){
            if(nums[i] > 0 && nums[i] < nums.size() && nums[nums[i]-1]!=nums[i]){
                swap(nums[i],nums[nums[i]-1]);
               
            } 
            else i++;
        }
        for(int i=0;i < nums.size();i++){
            if(i+1!=nums[i]) return i+1;
        }
        //if all the positive numbers from 1 to n are present, then ans will be n+1.
        return nums.size()+1;
    }
};
```

# [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
Intuition: 
In this problem we only have to bring unique element of in the front.
**Example** :arr= [0,0,1,1,1,2,2,3,3,4]
- i=0:
    - j=1 and nums[j]=nums[i] = 0
    - j=2 and nums[j]!=nums[i], so i++
Now the array will be arr = [0,1,1,1,1,2,2,3,3,4]
- i=1:
    - j=3 and nums[j]=nums[i]=1
    - j=4 and nums[j]=nums[i]=1
    - j=5 and nums[j]!=nums[i], so i++
 Now the array will be arr = [0,1,2,1,1,2,2,3,3,4]
 And so on...
 
**Code:**
```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i = 0;
        for (int j = 1; j < nums.size(); j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }
};
```

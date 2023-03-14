# [Two Sum](https://leetcode.com/problems/two-sum)

### Approach :
The Brute Force approach is to iterate through the array and, for each element, check if there is another element
in the array that adds up to the target value with the current element. However, this would take O(n^2) time complexity, which is not efficient for larger input arrays.

A better approach is to use a hash table to store the values we have already seen while iterating through 
the array. We can iterate through the array and, for each element, calculate the diifernce between that element
and the target value. We can then check if the difference is already in the hash table. 
If it is, then we have found a pair of indices that add up to the target value.
If not, we can add the current element to the hash table and continue iterating through the array.

### Time Complexity: O(N)
### Space Complexity :O(N)

**Input**: nums = [3, 7, 4, 9, 2], _target_ = 11
mp=[]
1. i=0, nums[i]=3, diff= 8 --> mp[3:0]
2. i=1, nums[i]=7, diff= 4 --> mp[3:0 , 7:1]
3. i=2, nums[i]=4, diff= 7 --> 7 is present in mp
 so, _output_ = [1,2]

**Code** :
#
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> mp;
        for (int i = 0; i < nums.size(); i++) {
            int diff = target - nums[i];
            if (mp.find(diff) != mp.end()) {
                return { mp[diff], i };
            }
            mp[nums[i]] = i;
        }
        return {};
    }
};
```

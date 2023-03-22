# [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
The class Solution implements a function subarraySum which takes a vector of integers nums and an integer k as input, and returns the number of subarrays whose sum equals k.

The intuition behind this solution is to use a hash map to keep track of the cumulative sum of the elements of the vector up to each index. At each index, we check if the current sum minus k exists in the hash map, and if it does, we add the count of the number of times that sum has occurred to the answer.

The approach to implement this is to first initialize two variables su and ans to 0, and an unordered map mp to store the cumulative sums and their frequencies. Then, we iterate through the vector nums and at each index i, we add the value of nums[i] to su to calculate the cumulative sum up to that index. We then check if su equals k, and if it does, we increment the answer variable ans.

Next, we check if mp contains the key su-k. If it does, it means that there is a subarray whose sum is equal to k and ends at the current index. We add the frequency of that sum to the answer ans. Finally, we increment the frequency of the current sum in the map mp.

After iterating through all the elements in nums, we return the final value of ans, which represents the number of subarrays whose sum is equal to k. The time complexity of this solution is O(n), where n is the size of the input vector nums.
**Code:**
```
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int su =0;
        int ans=0;
        unordered_map <int,int> mp;
        for(int i=0;i < nums.size();i++){
            su+=nums[i];
            if(su==k){
                ans++;
            }
            if(mp.find(su-k)!=mp.end()){
                ans+=mp[su-k];
            }
            mp[su]++;
        }
        return ans;
    }
};
```

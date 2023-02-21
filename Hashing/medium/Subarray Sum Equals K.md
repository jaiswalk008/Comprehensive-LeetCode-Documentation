# [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)

<pre>
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
</pre>

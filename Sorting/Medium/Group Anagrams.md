# [Group Anagrams](https://leetcode.com/problems/group-anagrams/)

### Approach:
- As Anagrams have same number of letters so sorting two anagrams will make the two strings identical.
- Using map to store the anagrams of each type.

**Code:**
```
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> res;
        unordered_map<string,vector<string>> mp;
        for(string s :strs){
            string temp=s;
            sort(temp.begin(),temp.end());
            mp[temp].push_back(s);
        }
        int i=0;
        for(auto it=mp.begin();it!=mp.end();it++){
            res.push_back(mp[it->first]);
        }
        return res;
    }
};
```

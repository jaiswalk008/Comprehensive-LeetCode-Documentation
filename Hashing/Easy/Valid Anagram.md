# [Valid Anagram](https://leetcode.com/problems/valid-anagram/)



<pre>
class Solution {
public:
    bool isAnagram(string s, string t) {
        int freq1[26]={0};
        int freq2[26]={0};
        if(s.length() != t.length()) return false;
        for(int i=0;i < s.size();i++){
            freq1[s[i]-'a']++;
            freq2[t[i]-'a']++;
        }
        bool flag =true;
        for(int i=0; i <26;i++){
            if(freq1[i]!=0 || freq2[i]!=0){
                if(freq1[i]!=freq2[i]){
                    flag =false;
                    break;
                }
            }
        }
        return flag;
    }
};
</pre>

# [Count the Number of Consistent Strings](https://leetcode.com/problems/count-the-number-of-consistent-strings/)

### Approach : 
We are going to check which characters are present in the **_allowed_** array. After that we will traverse each character of 
the _string_ present in the **_words_** array.

#### Note: Each character has some ASCII value in C++. So _a-a_ = 0 and _b-a_ =1.


C++ code : 
<pre>
class Solution {
public:
    int countConsistentStrings(string allowed, vector<string>& words) {
        int freq[26] = {0};
        for(char i: allowed) freq[i-'a']++;
        int ct =0;
        bool flag;
        for(string s : words){
            flag = true;
            for(char c : s){
                if(freq[c-'a']==0){
                    flag = false;
                    break;
                }
            }
            if(flag) ct++;
        }
        return ct;
    }
};
</pre>

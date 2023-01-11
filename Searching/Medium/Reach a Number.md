# [Reach a Number](https://leetcode.com/problems/reach-a-number/)

<pre>
class Solution {
public:
    int reachNumber(int target) {
        int s=0,ans=0;
        target = abs(target);
        while(s < target){
           ans++;
           s+=ans;
        }
        while((s-target)%2!=0){
            ans++;
            s+=ans;
        }
        return ans;
    }
};
</pre>

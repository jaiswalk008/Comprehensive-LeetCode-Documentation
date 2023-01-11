# [Sqrt(x)](https://leetcode.com/problems/sqrtx/)

<pre>
class Solution {
public:
    int mySqrt(int x) {
        unsigned long long int l = 1;
        unsigned long long int h = x;
        unsigned long long int mid;
        if(x<1) return 0;
        
        while(true){
            mid = l+(h-l)/2;
            
            unsigned long long int t= mid+1;
            if(((unsigned long long int)mid*mid)>x) h = mid;
            else if((unsigned long long int)(t*t)==x) return t;
            else if((unsigned long long int)(t*t)>x) return mid;
            else l = mid;
        }
        return mid;
    }
};
</pre>

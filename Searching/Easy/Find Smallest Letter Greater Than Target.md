# [Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

#### idea: Whenever the input is in sorted order, chances are higher that we need to use Binary Search.


***We should use mid = low + (high-low)/2 instead of mid = (low+high)/2 because the latter can result in integer overflow.***

**Example:** low = 1170105034 \
high = 1347855270 \
(low + high) / 2 //outputs  -888503496 \
low + (high - low) / 2 //outputs 1258980152 

##### Logic: Here we will use a modified Binary search algorithm and keep searching until the **_low_** bound becomes larger than the **_upper_** bound. Check for the edge case.
##### Since we need to return the element greater than the target so if the element is greater than or equal to the target we will increment **_low_** otherwise decrement **_high_**. 
##### This works even if the target is not present in the array because it narrows down the search for the element just bigger than the target. And will finally, return the element low is pointing to.

### Input: letters = ["c","e","f","f","g","g","g","g","k","m"] Targets : "a" , "f" , "h" , "p"

##### target : "a" ---> In this case the function will return "c" because the **if** condition will become _true_
##### target : "f" ---:
_low_ = 0 , _high_ = 9 , _mid_ = 4 , letters[mid] = "g"\
Now as "g" is _greater_ than the target so we will **_decrement_** _high_ as we do in Binary search\
_low_ = 0 , _high_ =3 , _mid_ = 1  , letters[mid] = "e"\
Now  "e" is _less_ than the target so we will **_increment_** _low_ \
_low_ = 2 , _high_ =3 , _mid_ = 2  , letters[mid] = "f"\
Now  "f" is _equal_ to the target but we will still **_increment_** _low_ as we need to find the element greater than the target\
_low_ = 3 , _high_ =3 , _mid_ = 3  , letters[mid] = "f"\
Now  "f" is _equal_ to the target but we will still **_increment_** _low_ as we need to find the element greater than the target and exit the loop
Now **_low_** = 4
##### the function will return letters[4] =  "g"

##### target : "h" ---:
**Note** : "h" is not _present_ in the array\
_low_ = 0 , _high_ = 9 , _mid_ = 4 , letters[mid] = "g"\
as "g" is _less_ than the target so we will **_increment_** _low_ \
_low_ = 5 , _high_ = 9 , _mid_ = 7 , letters[mid] = "g"\
as "g" is _less_ than the target so again we will **_increment_** _low_ \
_low_ = 8 , _high_ = 9 , _mid_ = 8 , letters[mid] = "k"\
Now as "k" is _greater_ than the target so we will **_decrement_** _high_ \
_low_ = 8 , _high_ = 7 ---> so here low becomes greater than the target so the control will exit from the loop
##### and the function will return letters[8] =  "k" 

##### target : "p" ---> In this case the function will return "m" because the **if** condition will become _true_ as "p" is greater than the last element which is "m"
<pre>
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        int low = 0, high = letters.size()-1, mid;
        
        //Edge Case : checking if the target is less than the first element or 
        //greater than the last element of the array.
        
        if(target < letters[0] || target >= letters[high]) return letters[0];
        while(low<=high){
            mid = low + (high-low)/2;
            if(target >= letters[2]) low = mid+1;
            else high = mid-1;
        }
        return letters[low];
    }
};
</pre>

# [Largest Number](https://leetcode.com/problems/largest-number/)

### Intuition
In this problem, first we have to convert each number to string and then concatenate them in such a way that the entire string becomes largest number possible.

### Approach
The custom sorting function is to prioritize the concatenation that results in the larger number. For example, given two strings s1 and s2, if s1+s2 is larger than s2+s1, then s1 should come before s2 in the sorted array. This logic is implemented in the comp function, which returns true if s1+s2 is greater than or equal to s2+s1.
for example, for 9 and 18 the two strings can be 918 and 189. As 918 is greater than 189 so 9 should be kept ahead of 18 in the sorting function.
The code also checks if all the integers in the input array are zero. If they are, then the result should be "0". Otherwise, the vector of strings is sorted and concatenated to form the final result.

### What is a  Comparator?
A comparator is a function that is used to define the order of elements in a container. It is typically used with sorting algorithms such as std::sort.

A comparator takes two arguments and returns a Boolean value indicating whether the first argument should come before or after the second argument in the sorted order

**Example:**
Suppose we have a vector of pairs vec where each pair contains a string name and an integer age. We want to sort the vector in ascending order based on the age field of each pair. We can use a custom comparator function to achieve this.
<pre>
bool cmp(const pair<string, int>& a, const pair<string, int>& b) {
    return a.second < b.second;
}
int main(){
    vector<pair<string, int>> vec = {{"Alice", 25}, {"Bob", 32}, {"Charlie", 18}};
    sort(vec.begin(), vec.end(), cmp);
}
 Result:
{ {"Charlie", 18}, {"Alice", 25}, {"Bob", 32} }
</pre>
The **cmp** function takes two arguments, which are both pairs of _string_ and _int_. It compares the _age_ field (second element) of each _pair_ and returns **true** if the first argument has a lower _age_ than the second argument. If the _age_ is equal or higher, it returns _false_. This means that the vector of pairs will be sorted in **ascending** order based on the _age_ field.


**C++ Code:**
<pre>
class Solution {
public:
    static bool comp(string s1,string s2){
        string temp1=s1+s2;
        string temp2=s2+s1;
        if(temp1>=temp2) return true;
        else return false;
    }
    string largestNumber(vector<int>& nums) {
        vector<string> str;
        bool zero=true;
        for(int n:nums){
            if(n!=0) zero=false;
            str.push_back(to_string(n));
        }
        string res="";
        if(zero) return "0";
        else{
            
            sort(str.begin(),str.end(),comp);
            for(string s:str) res+=s;
        }
        return res;
    }
    
};
</pre>
**Java Code:**
<pre>
class Solution {
    private class LargerNumberComparator implements Comparator<String> {
        @Override
        public int compare(String a, String b) {
            String order1 = a + b;
            String order2 = b + a;
           return order2.compareTo(order1);
        }
    }

    public String largestNumber(int[] nums) {
        // Get input integers as strings.
        String[] asStrs = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            asStrs[i] = String.valueOf(nums[i]);
        }

        // Sort strings according to custom comparator.
        Arrays.sort(asStrs, new LargerNumberComparator());

        // If, after being sorted, the largest number is `0`, the entire number
        // is zero.
        if (asStrs[0].equals("0")) {
            return "0";
        }

        // Build largest number from sorted array.
        String largestNumberStr = new String();
        for (String numAsStr : asStrs) {
            largestNumberStr += numAsStr;
        }

        return largestNumberStr;
    }
}
</pre>

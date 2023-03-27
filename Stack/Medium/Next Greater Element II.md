# [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii)

### Intuition:
- The intuition behind this approach is that if we encounter an element for which we have already found the next greater element, we do not need to consider it again in the second traversal, because its next greater element will not change. 
- By removing the indices of the elements that cannot be the next greater element of any element after them, we can reduce the size of the stack and improve the efficiency of the algorithm.
- The use of a stack ensures that we always have the indices of the elements in descending order of their values, which allows us to find the next greater element for each element efficiently.

### Approach:
- The approach used in the given code is to use a stack to store the indices of the elements in the input array, in descending order of their values.
We traverse the input array twice, once from the end to the beginning, and once from the beginning to the end.
- In the first traversal, we remove all the indices from the stack that correspond to elements smaller than or equal to the current element.
 We do this because those elements cannot be the next greater element of any element after them. After removing those indices, we push the current index onto the stack.
- In the second traversal, we again remove all the indices from the stack that correspond to elements smaller than or equal to the current element, but this time, if there is an index in the stack corresponding to an element greater than the current element, we store that element as the next greater element of the current element in the result vector.

**Code:**
```
class Solution {
public:
    vector<int> nextGreaterElements(vector<int>& nums) {
        int n = nums.size();
        vector <int> res(n,-1);
        stack <int> s;
        for(int i=0;i<2*n;i++){
            while(s.size()>0 && nums[i%n]>nums[s.top()]){
                res[s.top()] = nums[i%n];
                s.pop();
            }
            if(i<n) s.push(i);
        }   
        return res;
    }
};
```

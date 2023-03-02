# [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)
### Method 1:
### Intuition:
The intuition behind the algorithm is to use the fact that the array nums contains integers in the range
_[1, n]_, where n is the size of the array. Therefore, if there are no duplicate elements in nums, 
then each integer from 1 to n must appear exactly once in the array at the index corresponding to its value minus 1 (i.e., the integer 1 should appear at index 0, the integer 2 should appear at index 1, and so on).

### Approach:
The algorithm works by iterating through the array nums and swapping elements to their correct positions 
until a duplicate element is found. More specifically, the algorithm maintains an index i that 
starts at 0 and is incremented by 1 at each iteration of the loop. At each iteration, the algorithm 
checks whether the element at index i is already in its correct position (i.e., whether nums[i] == i+1). 
If it is, then we move on to the next index i.

If the element at index i is not in its correct position, then there are two possibilities:
either the element at index i is a duplicate element, or it is not. 
To check whether it is a duplicate element, we compare it to the element at the index corresponding to its value minus 1 (i.e., nums[nums[i]-1]). 
If they are equal, then we have found a duplicate element, and we return it. If they are not equal, 
then we swap the elements at indices i and nums[i]-1, so that the element at index i is moved to its correct position,
and we repeat the process with the new element at index i.

The swapping of elements ensures that we maintain the property that each integer from 1 to n appears exactly once in the array
at the index corresponding to its value minus 1. Therefore, if there are no duplicate elements,
then the algorithm will eventually iterate through the entire array without finding any duplicates and return 0.

### Time Complexity:
The time complexity of the algorithm is O(n), where n is the size of the input vector.
The worst-case scenario is when the duplicate element is the last element in the array, 
in which case the algorithm needs to iterate through the entire array to find it. However, in practice, 
the algorithm is likely to find the duplicate element much sooner, and the average-case and best-case time complexity are therefore lower than O(n).

#### Input : _[1,3,4,2,2]_
1. As 1 is in the correct position so for _i=0_ and _nums[0]-1_ is also 0.
2. Now 3 is at index 2 so we will swap it with the element at index 3 so that 3 will be at the correct position and will keep doing
it till 2 comes at index 2
_[1,3,4,2,2]_ --> _[1,4,3,2,2]_ --> _[1,2,3,4,2]_
3.Now as 2 is at the correct index so _i_ will be incremented and same will happen for 3 and 4 .
4. When we reach at the last index we will see that _nums[i]_ and _nums[nums[i]-1]_ will be equal which confirms nums[i] is the duplicate number

#### Code for Method 1:
<pre>
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int i=0;
        while(i < nums.size()){
            if(i==(nums[i]-1) ) i++;
            else if(i!=(nums[i]-1) && nums[i]==nums[nums[i]-1]) return nums[i];
            else{
                int temp=nums[nums[i]-1];
                nums[nums[i]-1]=nums[i];
                nums[i] = temp;
            }
        }
        return 0;
    }
};
</pre>

### Method 2:

### Intuition:
The intuition behind this approach is that we can use the array itself as a way to keep track of which elements
we have seen before. By changing the sign of the element at index abs(nums[i])-1, we mark that we have seen the element
abs(nums[i]). If we encounter the same element again, the element at index abs(nums[i])-1 will already be negative, indicating that we have seen it before.

### Approach:
The approach to solving the problem of finding the duplicate element in a given array by changing the sign of the elements:

1.Traverse the input array nums.\
2.For each element nums[i], if the element at index abs(nums[i])-1 is positive, then change its sign to negative.
Otherwise, abs(nums[i]) is the duplicate element, so return it.\
3.If no duplicate element is found after traversing the entire array, return -1.

#### Input : _[3, 1, 3, 4, 2]_

1. We start by traversing the array from left to right.
2. We begin with the first element 3. 
We access the element at index abs(3)-1, which is 2. Since nums[2] is positive, we change its sign to negative.
The array now becomes: _[3, 1, -3, 4, 2]_\
3.Next, we move to the second element 1. We access the element at index abs(1)-1, which is 0. Since nums[0] is positive, we change its sign to negative. 
The array now becomes: _[-3, 1, -3, 4, 2]_\
4.We continue this process for the rest of the elements. When we reach the third element 3 again, 
we access the element at index abs(3)-1, which is 2. Since nums[2] is negative, we know that we have seen the element 3 
before and it is the duplicate element. Therefore, we return 3.

### Code for Method 2:
<pre>
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        for (int i = 0; i < nums.size(); i++) {
            int index = abs(nums[i]) - 1;
            if (nums[index] > 0) {
                nums[index] = -nums[index];
            } else {
                return abs(nums[i]);
            }
        }
        return -1;
    }
};
</pre>

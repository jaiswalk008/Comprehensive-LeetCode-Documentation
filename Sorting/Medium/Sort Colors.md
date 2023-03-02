# [Sort Colors](https://leetcode.com/problems/sort-colors/description/)

### Method 1:
### Approach: 
  - The algorithm used in this code is called the "Dutch National Flag" algorithm, 
which is an efficient way to sort an array containing only a small number of distinct values.
  - The code uses an array of size 3 to count the occurrences of each value in the input array. 
  - It then clears the input array and rebuilds it by iterating through the count array and adding the corresponding 
value to the input array the correct number of times.

### Code : 
<pre>
class Solution {
public:
    void sortColors(vector<int>& nums) {
        long int arr[3]={0};
        for(int i=0;i < nums.size();i++){
            arr[nums[i]]+=1;
        }
        nums.clear();
        for(int i=0;i < 3;i++){
            for(int j=0;j < arr[i];j++){
                nums.push_back(i);
            }
        }
    }
};
</pre>

### Method 2:
### Intuition:
  - The algorithm aims to partition the array into three sections: the section containing 0s, the section containing 1s, and the section containing 2s.
  - We can achieve this partition by maintaining three pointers: start, last, and i. 
  - Initially, start points to the first element of the array, last points to the last element of the array, while i starts from 0 and moves towards the last element.
### Approach :

  - We traverse the array from left to right with the i pointer, 
    and we swap the current element with the element pointed to by the start pointer if the current element is 0.
  - We then move both the start and i pointers to the right.
  - Similarly, if the current element is 2, we swap the current element with the element pointed to by the last pointer 
    and move the last pointer to the left. However, we don't move the i pointer in this case since the swapped element needs to be re-checked.
  - If the current element is 1, we simply move the i pointer to the right.
  - We repeat this process until the i pointer crosses the last pointer, which means that the entire array has been partitioned into three sections.
  
### Input : _nums = [2,0,2,1,1,0]_
  - Initially, start points to the first element (2) and last points to the last element (0) of the array, while i starts from 0.
  - We compare the element pointed to by i (2) with 0, 1, and 2.
  - Since nums[i] is 2, we swap nums[i] with nums[last], and decrement last. The array becomes [2,0,0,1,1,2], and last becomes 4.
  - Now, we compare the element pointed to by i (0) with 0, 1, and 2.
  - Since nums[i] is 0, we swap nums[i] with nums[start], and increment both start and i. The array becomes [0,2,0,1,1,2], and start becomes 1 and i becomes 1.
  - Now, we compare the element pointed to by i (2) with 0, 1, and 2.
  - Since nums[i] is 0, we swap nums[i] with nums[start], and increment both start and i. The array becomes [0,0,2,1,1,2], and start becomes 2 and i becomes 2.
  - Now, we compare the element pointed to by i (1) with 0, 1, and 2.
  - Since nums[i] is 1, we simply increment i.
  - Now, we compare the element pointed to by i (1) with 0, 1, and 2.
  - Since nums[i] is 1, we simply increment i.
  - Now, we compare the element pointed to by i (2) with 0, 1, and 2.
  - Since nums[i] is 2, we swap nums[i] with nums[last], and decrement last. The array becomes [0,0,1,1,2,2], and last becomes 3.
  - Now, i > last, which means the array has been sorted into three sections: the section containing 0s (from index 0 to index start - 1), the section containing 1s (from index start to index i - 1), and the section containing 2s (from index i to index last).
  
  ### Code : 
  <pre>
  class Solution {
public:
    void sortColors(vector<int>& nums) {
        int start=0,last=nums.size()-1,i=0;
        while(i <= last){
            if(nums[i]==0){
                swap(nums[i++],nums[start++]);
            }
            else if(nums[i]==2){
                swap(nums[i],nums[last--]);
            }
            else i++;
        }
    }
};
</pre>

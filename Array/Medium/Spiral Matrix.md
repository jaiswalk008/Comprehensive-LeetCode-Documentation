# [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

### Approach:
1. We start by initializing four pointers: left, right, up, and down. The left and right pointers keep track of the first and last column of the matrix that we need to visit, while the up and down pointers keep track of the first and last row of the matrix that we need to visit.

2. We also initialize an empty vector called ans, which will store the elements of the matrix in the spiral order.

3. We then enter a while loop that runs until we have visited all the elements of the matrix.

4. Within the while loop, we have four for loops that traverse the matrix in the desired order.

    - The first for loop traverses the first row from left to right and adds each element to the ans vector.

    - The second for loop traverses the last column from top to bottom, excluding the first and last elements (which were already visited in the first and third loops), and adds each element to the ans vector.

    - The third for loop traverses the last row from right to left, excluding the first and last elements (which were already visited in the first and second loops), and adds each element to the ans vector.

    - The fourth for loop traverses the first column from bottom to top, excluding the first and last elements (which were already visited in the second and third loops), and adds each element to the ans vector.

5. After each for loop, we update the left, right, up, and down pointers to exclude the elements that were already visited.

6. We keep repeating this process until we have visited all the elements in the matrix.

7. Finally, we return the ans vector containing the elements of the matrix in the spiral order.
<pre>
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> ans;
        
        int n=matrix[0].size();//number of columns
        
        int m = matrix.size();//number of rows
        int left=0,right=n-1,up=0,down=m-1;
        
        int elements = m*n;
        while(ans.size() < elements ){
            /* 1 2 3
               4 5 6 
               7 8 9*/
            //for loop for traversing from left to right(1 2 3)
            for(int i=left;i <= right && ans.size() < elements ;i++ )
                ans.push_back(matrix[up][i]);
               
           
            //for loop for traversing from top to bottom(6)
            for(int i=up+1;i <= down-1 && ans.size() < elements;i++)
                ans.push_back(matrix[i][right]);

            
            //for loop for traversing from right to left ( 9 8 7)
            for(int i=right;i>=left && ans.size() < elements;i--) 
                ans.push_back(matrix[down][i]);
           
            //for loop for traversing from right to left (4)
            for(int i=down-1;i>up && ans.size() < elements;i--) 
                ans.push_back(matrix[i][left]);
            // 5 will be inserted after this updating the pointers
            left++; up++; down--; right--;
        }
        return ans;
      
    }
};
</pre>

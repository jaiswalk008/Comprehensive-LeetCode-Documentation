# [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)


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

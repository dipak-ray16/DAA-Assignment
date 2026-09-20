#LEETCODE 74 : SEARCH A 2D MATRIX SOLUTION : 

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
       int m = matrix.size();
       int n = matrix[0].size();

       int l = 0;
       int h = m * n - 1;
       while(l <= h){
        int mid = l + (h - l) / 2;
        int row = mid / n;
        int col = mid % n;
        if(matrix[row][col] == target) return true;
        else if(target > matrix[row][col]) l = mid + 1;
        else h = mid - 1;
       } 
       return false;
    }
};

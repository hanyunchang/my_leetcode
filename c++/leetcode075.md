```
class Solution {
public:
    /**
     * 
     * @param matrix int整型vector<vector<>> 
     * @param target int整型 
     * @return bool布尔型
     */
    bool searchMatrix(vector<vector<int> >& matrix, int target) {
        // write code here
        if(matrix.size() == 0 || matrix[0].size() == 0) {
            return false;
        }
        int start = 0, end = matrix.size() * matrix[0].size() - 1;
        while(start <= end) {
            int mid = (start + end) / 2;
            int mid_val = matrix[mid / matrix[0].size()][mid % matrix[0].size()];
            if(mid_val == target) {
                return true;
            }

            if(mid_val > target) {
                end = mid - 1;
            }else {
                start = mid + 1;
            }
        }
        return false;
    }
};
```

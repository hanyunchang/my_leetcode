```
class Solution {
public:
    void setZeroes(vector<vector<int> > &matrix) {
        if(matrix.size() == 0 || matrix[0].size() == 0) {
            return ;
        }
        bool col_flag = false, row_flag = false;
        for(int i = 0; i < matrix[0].size(); i++) {//row
            if(matrix[0][i] == 0) {
                row_flag = true;
                break;
            }
        }

        for(int i = 0; i < matrix.size(); i++) {//col
            if(matrix[i][0] == 0) {
                col_flag = true;
                break;
            }
        }

        for(int i = 1; i < matrix.size(); i++) { //注意这里要从1开始
            for(int j = 1; j < matrix[0].size(); j++) {//注意这里要从1开始
                if(matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }

        for(int i = 1; i < matrix.size(); i++) {//注意这里要从1开始
            for(int j = 1; j < matrix[0].size(); j++) {//注意这里要从1开始
                if(matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }       
        
        if(row_flag){
            for(int i = 0; i < matrix[0].size(); i++) {//row
                matrix[0][i] = 0;
            }
        }

        if(col_flag) {
            for(int i = 0; i < matrix.size(); i++) {
                matrix[i][0] = 0;
            }
        }
    }
};

```

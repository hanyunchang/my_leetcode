class Solution {
public:
    int minimumTotal(vector<vector<int> > &triangle) {
        if(triangle.size() <= 0 || triangle[0].size() <= 0) {
            return 0;
        }

        for(int row_index = triangle.size() - 2; row_index >= 0; row_index--) {
            for(int col_index = 0; col_index < triangle[row_index].size(); col_index++) {
                int min_num = min(triangle[row_index + 1][col_index], triangle[row_index + 1][col_index + 1]);
                triangle[row_index][col_index] += min_num;
            }
        }
        return triangle[0][0];
    }
};
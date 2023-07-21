
class Solution {
public:
    /**
     * 
     * @param rowIndex int整型 
     * @return int整型vector
     */
    vector<int> getRow(int rowIndex) {
        // write code here
        vector<int> row(rowIndex + 1);
        row[0] = 1;
        for(int cur_index = 1; cur_index <= rowIndex; cur_index++){
            int prev_val = row[0];
            for(int i = 1; i <= cur_index + 1; i++) {
                int tmp = row[i] + prev_val;
                prev_val = row[i];
                row[i] = tmp;
            }
        }
        return row;
    }
};
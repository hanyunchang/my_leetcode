```
#include <algorithm>
#include <vector>
class Solution {
public:
    bool flag = false;
    bool exist(vector<vector<char> > &board, string word) {
        for(int i = 0; i < board.size(); i++) {
            for(int j = 0; j < board[i].size(); j++) {
                if(search(board, word, i, j)) {
                    return true;
                }
            }
        }
        return false;
    }
  
    vector<int> delta_col = {1, -1, 0, 0};
    vector<int> delta_row = {0, 0, -1, 1};
    bool search(vector<vector<char>> &board, string word, int row_index, int col_index) {
        if(word.empty()) {
            return true;
        }
        if(row_index < 0 || row_index >= board.size() || col_index < 0 || col_index >= board[row_index].size()) {
            return false;
        }
        if(word[0] != board[row_index][col_index]) {
            return false;
        }
        
        char c = board[row_index][col_index];
        board[row_index][col_index] = '#';
        
        for(int i = 0; i < 4; i++) {
            if(search(board, word.substr(1, word.size() - 1), row_index + delta_row[i], col_index + delta_col[i])) {
                return true;
            }
        }
        board[row_index][col_index] = c;
        return false;
    }

};
```

* vector的初始化
vector<int> v = {0, 1};
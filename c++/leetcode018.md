```
class Solution {
public:
    void solve(vector<vector<char>> &board) {
        if(board.size() == 0 || board[0].size() == 0) {
            return ;
        }
        int row = 0;
        for(int col = 0; col < board[0].size(); col++){
            if(board[row][col] == 'O') {
                DFS(row, col, board);
            }
        }

        row = board.size() - 1;
        for(int col = 0; col < board[0].size(); col++){
            if(board[row][col] == 'O') {
                DFS(row, col, board);
            }
        }

        int col = 0;
        for(int row = 0; row < board.size(); row++) {
            if(board[row][col] == 'O') {
                DFS(row, col, board);
            }
        }
        col = board[0].size() - 1;
        for(int row = 0; row < board.size(); row++) {
            if(board[row][col] == 'O') {
                DFS(row, col, board);
            }
        }

        for(int row = 0; row < board.size(); row++) {
            for(int col = 0; col < board[0].size(); col++) {
                if(board[row][col] == 'O'){
                    board[row][col] = 'X';
                }else if(board[row][col] == '#'){
                    board[row][col] = 'O';
                }
            }
        }
    }

    void DFS(int row_index, int col_index, vector<vector<char>> &board) {
        if(row_index < 0 || row_index > board.size() - 1 || col_index < 0 || col_index > board[0].size() - 1){
            return ;
        }
        if(board[row_index][col_index] != 'O'){
            return ;
        }

        board[row_index][col_index] = '#';
        DFS(row_index + 1, col_index, board);
        DFS(row_index - 1, col_index, board);
        DFS(row_index, col_index + 1, board);
        DFS(row_index, col_index - 1, board);
    }
};
```
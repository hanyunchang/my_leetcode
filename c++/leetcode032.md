```

#include <stdexcept>
#include <vector>
class Solution {
public:
    /**
     * 
     * @param S string字符串 
     * @param T string字符串 
     * @return int整型
     */
    int numDistinct(string S, string T) {
        // write code here
        vector<vector<int>> dp(T.size() + 1, vector<int>(S.size() + 1));
        for(auto& val : dp[0]){
            val = 1;
        }

        for(int T_len = 1; T_len <= T.size(); T_len++) {
            for(int S_index = 0; S_index < S.size(); S_index++) {
                if(T[T_len - 1] == S[S_index]) {
                    dp[T_len][S_index + 1] = dp[T_len][S_index] + dp[T_len - 1][S_index]; 
                } else{
                    dp[T_len][S_index + 1] = dp[T_len][S_index];
                }
            }
        }
        return dp[T.size()][S.size()];
    }
};
```
* dp可以推出来, 但是代码由于要考虑到dp的初始状态和数组越界, 就还挺绕的
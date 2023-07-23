```

#include <vector>
class Solution {
public:
    /**
     * 
     * @param s1 string字符串 
     * @param s2 string字符串 
     * @param s3 string字符串 
     * @return bool布尔型
     */
    bool isInterleave(string s1, string s2, string s3) {
        if(s1.size() + s2.size() != s3.size()) { //不可省
            return false;
        }

        vector<vector<bool>> dp(s1.size() + 1, vector<bool>(s2.size() + 1));
        //dp[i][j] : len_i of s1 + len_j of s2 ==> s3
        dp[0][0] = true;
        for(int i = 1; i <= s1.size(); i++){
            if(s1[i - 1] == s3[i - 1]){
                dp[i][0] = dp[i - 1][0];
            }
        }

        for(int j = 1; j <= s2.size(); j++) {
            if(s2[j - 1] == s3[j - 1]) {
                dp[0][j] = dp[0][j - 1];
            }
        }
        
        for(int i = 1; i <= s1.size(); i++) {
            for(int j = 1; j <= s2.size(); j++) {
                if(dp[i - 1][j] && s1[i - 1] == s3[i + j - 1]) {
                    dp[i][j] = true;
                }
                if(dp[i][j - 1] && s2[j - 1] == s3[i + j - 1]) {
                    dp[i][j] = true;
                }
            }
        }
        
        return dp[s1.size()][s2.size()];

    }
};
```
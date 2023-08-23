```

class Solution {
public:
    /**
     * 
     * @param word1 string字符串 
     * @param word2 string字符串 
     * @return int整型
     */
     //dp
    int minDistance(string word1, string word2) {
        // write code here
        //word1 -> word2
        //dp[i][j]  == the answer of [pre i of word1 -> pre j of word2]
        vector<vector<int>> dp(word1.size() + 1, vector<int>(word2.size() + 1));
        for(int i = 0; i < dp.size(); i++) {
            dp[i][0] = i;
        }
        for(int j = 0; j < dp[0].size(); j++) {
            dp[0][j] = j;
        }
        
        for(int i = 1; i < dp.size(); i++) {
            for(int j = 1; j < dp[0].size(); j++) {
                if(word1[i - 1] == word2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1];
                }else{//对于word1最后一个字符有三种操作，替换、删除、插入
                    int choice_a = dp[i - 1][j - 1] + 1;//替换
                    int choice_b = dp[i - 1][j] + 1;//删除
                    int choice_c = dp[i][j - 1] + 1;//插入
                    dp[i][j] = min(choice_a, min(choice_b, choice_c));
                }
            }
        }
        return dp[word1.size()][word2.size()];
    }
};
```

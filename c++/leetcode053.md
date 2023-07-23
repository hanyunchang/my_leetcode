```
class Solution {
public:
    /**
     * 
     * @param n int整型 
     * @return int整型
     */
    //注意好下标的含义
    int numTrees(int n) {
        // write code here
        vector<int> dp(n + 1);
        //dp[i] => i个元素
        dp[0] = 1;
        for(int i = 1; i <= n; i++) {
            for(int j = 1; j <= i; j++) {
                dp[i] += (dp[j - 1] * dp[i - j]);
            }
        }
        return dp[n];
    }
};
```
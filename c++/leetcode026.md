```
#include <vector>
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param prices int整型vector 
     * @return int整型
     */
    int maxProfit(vector<int>& prices) {
        // write code here
        if(prices.size() < 2) {
            return 0;
        }
        vector<int> dp(prices.size());
        dp[0] = 0;
        int min_price = prices[0];
        for(int i = 1; i < prices.size(); i++) {
            dp[i] = max(dp[i-1], prices[i] - min_price);
            min_price = min(min_price, prices[i]);
        }
        return dp[prices.size() - 1];
    }
};
```
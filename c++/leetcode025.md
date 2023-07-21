```
class Solution {
public:
    /**
     * 
     * @param prices int整型vector 
     * @return int整型
     */
    int maxProfit(vector<int>& prices) {
        int sum = 0;
        for(int i = 1; i < prices.size(); i++) {
            if(prices[i] > prices[i-1]){
                sum += prices[i] - prices[i-1];
            }
        }
        return sum;
    }
};
```
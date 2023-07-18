```

#include <vector>
class Solution {
public:
    /**
     * 
     * @param ratings int整型vector 
     * @return int整型
     */
     /**
     反证法证明：
     思路见：https://leetcode.cn/problems/candy/solution/fen-fa-tang-guo-by-powcai/
     这不是什么贪心算法，只是分两步走，第一步求出确认的，不确认的到第二步解决
     */
    int candy(vector<int>& ratings) {
        // write code here
        vector<int> candies(ratings.size(), 1);
        for(int i = 1; i < ratings.size(); i++){
            if(ratings[i] > ratings[i-1]) {
                candies[i] = candies[i-1] + 1;
            }
        }
        for(int i = ratings.size() - 2; i >= 0; i--){
            if(ratings[i] > ratings[i+1] && candies[i] <= candies[i+1]) {
                candies[i] = candies[i+1] + 1;
            }
        }
        int sum = 0;
        for(int i = 0; i < candies.size(); i++) {
            sum += candies[i];
        }
        return sum;
    }
};
```

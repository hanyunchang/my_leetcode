```

#include <cmath>
class Solution {
public:
    /**
     * 
     * @param gas int整型vector 
     * @param cost int整型vector 
     * @return int整型
     */
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        // write code here
        int left_of_stage = 0;
        int left_of_all = 0;
        int index = 0;
        for(int i = 0; i < gas.size(); i++) {
            left_of_stage += gas[i] - cost[i];
            left_of_all += gas[i] - cost[i];
            if(left_of_stage < 0) {
                left_of_stage = 0;
                index = i + 1;
            }
        }
        return left_of_all >= 0 ? index : -1;
    }
};
```

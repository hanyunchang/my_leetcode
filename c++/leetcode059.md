* 解法1
```

class Solution {
public:
    /**
     * 
     * @param n int整型 
     * @return int整型vector
     */
    //思路 序列(n - 1) => 序列(n)
    // 具体方法是对序列(n - 1)分别在前面增加0、1生成两波数据，然后粘合在一起(至于为什么能粘合在一起, 稍微想一下就能明白)
    vector<int> grayCode(int n) {
        // write code here
        vector<int> res;
        if(n == 0) {//0的时候是0我真是服了
            res.push_back(0);
            return res;
        }
        if(n == 1) {
            res.push_back(0);
            res.push_back(1);
            return res;
        }
        for(auto k : grayCode(n -1)){
            res.push_back(k);
        }

        int half_size = res.size();
        int tool_num = pow(2, n - 1);
        for(int i = half_size - 1; i >= 0; i--) {
            int val = res[i] | tool_num;
            res.push_back(val);
        }

        return res;
    }
};
```

* 解法二

```
class Solution {
public:
    /**
     *
     * @param n int整型
     * @return int整型vector
     */
    vector<int> grayCode(int n) {
        // write code here
        vector<int> res(1, 0);
        for (int i = 0; i < n; ++i) {
            int topBit = 1 << i;
            for (int j = res.size() - 1; j >= 0; --j) {
                res.push_back(topBit | res[j]);
            }
        }
        return res;
    }
};
```
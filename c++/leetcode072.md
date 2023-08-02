```

#include <vector>
class Solution {
public:
    /**
     * 
     * @param n int整型 
     * @param k int整型 
     * @return int整型vector<vector<>>
     */
    //集合题目的变种
    vector<vector<int> > combine(int n, int k) {
        // write code here
        vector<int> tmp;
        vector<vector<int>> res;
        FS(0, 0, n, k, tmp, res);
        return res;
    }

    void FS(int size, int prev_num, int n, int k, vector<int>& tmp, vector<vector<int>>& res) {
        if(size == k) {
            res.push_back(tmp);
            return ;
        }

        for(int num = prev_num + 1; num <= n; num++) {
            tmp.push_back(num);
            FS(size + 1, num, n, k, tmp, res);
            tmp.pop_back();
        }
    }
};
```
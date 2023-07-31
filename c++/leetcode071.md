```
#include <vector>
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param S int整型vector 
     * @return int整型vector<vector<>>
     */
     //子集2的变种
    vector<vector<int> > subsets(vector<int>& S) {
        // write code here
        vector<vector<int>> res;
        vector<int> tmp;
        DFS(S, tmp, -1, res);
        return res;
    }

    void DFS(vector<int>& S, vector<int>& tmp, int prev_index, vector<vector<int>>& res) {
        res.push_back(tmp);
        
        for(int i = prev_index + 1; i < S.size(); i++) {
            tmp.push_back(S[i]);
            DFS(S, tmp, i, res);
            tmp.pop_back();
        }
    }
};
```
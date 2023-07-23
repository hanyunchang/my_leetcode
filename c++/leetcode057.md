```
#include <iterator>
class Solution {
public:
   
    //思路:
    //如果我们得到了长度为k的所有不重复子集，那么我们便可以由此生成所有长度为k+1的不重复子集
    //步骤是：对于每一个k子集，我们只从其最大下标以后的元素挑选，并且对于相同的元素只组装一次，组装成k+1的集合
    //反证法可证明1.得到的是全部的k+1子集 2.不存在重复的k+1子集
    vector<vector<int> > subsetsWithDup(vector<int> &S) {
        sort(S.begin(), S.end());
        vector<vector<int>> res;
        vector<int> subset;
        subsetsWithDup_(S, 0, subset, res);
        return res;
    }

    void subsetsWithDup_(vector<int> &S, int begin_index, vector<int>& subset, vector<vector<int>>& res){
        res.push_back(subset);
        

        for(int index = begin_index; index < S.size(); index++) {
            if(index != begin_index && S[index] == S[index - 1]){
                continue;
            }

            subset.push_back(S[index]);
            subsetsWithDup_(S, index + 1, subset, res);
            subset.pop_back();
        }
    }
};
```
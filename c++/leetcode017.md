```

#include <vector>
class Solution {
public:
    /**
     * 
     * @param s string字符串 
     * @return string字符串vector<vector<>>
     */
    vector<vector<string> > partition(string s) {
        // write code here
        vector<string> vec;
        vector<vector<string>> res;
        DFS(s, vec, res);
        return res;
    }
    
    void DFS(string str, vector<string>& tmp, vector<vector<string>>& res) {
        if(str.empty()) {
            res.push_back(tmp);
        }
        for(int len = 1; len <= str.length(); len++) {
            if(is_huiwen(str.substr(0, len))){
                tmp.push_back(str.substr(0, len));
                DFS(str.substr(len, str.length() - len), tmp, res);
                tmp.pop_back();
            }
        }
    }

    bool is_huiwen(string str){
        int l_index = 0;
        int r_index = str.length() - 1;
        while(l_index <= r_index) {
            if(str[l_index] != str[r_index]) {
                return false;
            }
            l_index++; r_index--;
        }
        return true;
    }
};
```
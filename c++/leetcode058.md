```

class Solution {
public:
    /**
     * 
     * @param s string字符串 
     * @return int整型
     */
    int numDecodings(string s) {
        if(s.size() == 0) {
            return 0;
        }
        // write code here
        //dp[i]: the len(i) of s 的解法
        vector<int> dp(s.size());
        if(s[0] > '0' && s[0] <= '9'){
            dp[0] = 1;
        }else {
            dp[0] = 0;
        }

        for(int i = 1; i < s.size(); i++) {
            if(s[i] > '0' && s[i] <= '9') {
                dp[i] += dp[i - 1];
            }
            if(is_valid(s[i - 1], s[i])) {
                if(i == 1){
                    dp[i] += 1;
                }else {
                    dp[i] += dp[i - 2];
                }
            }
        }

        return dp[s.size() - 1];
    }

    bool is_valid(char a, char b){
        int val = (a - '0') * 10 + (b - '0');
        return 10 <= val && val <= 26;
    }
};
```
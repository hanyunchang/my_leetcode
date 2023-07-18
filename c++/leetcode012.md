
class Solution {
public:
    /**
     * 
     * @param A int整型一维数组 
     * @param n int A数组长度
     * @return int整型
     */
    int singleNumber(int* A, int n) {
        // write code here
        int ones = 0;
        for(int i = 0; i < n; i++) {
            ones = ones ^ A[i];
        }
        return ones;
    }
};

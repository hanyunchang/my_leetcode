
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
        int twos = 0;
        for(int i = 0; i < n; i++) {
            int new_threes = A[i] & twos;
            //先把new_threes给摘掉
            int new_ones = A[i] ^ new_threes;
            ones = new_ones ^ ones;
            //先把new_threes给摘掉
            twos = twos ^ new_threes;
            twos = twos | (ones & new_ones);
        }
        return ones;

    }
};




------
* c++位移操作
  ![image](https://github.com/hanyunchang/my_leetcode/assets/40823439/f6884690-44ab-4ae5-8ce3-c1405a3e10cf)

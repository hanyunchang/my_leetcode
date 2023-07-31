```
class Solution {
public:
    /**
     * 
     * @param A int整型一维数组 
     * @param n int A数组长度
     * @param target int整型 
     * @return bool布尔型
     */

    //考虑这几种情况来判断一个区间是有序的还是旋转后的
    //1. end > start 那么这个区间一定是有序的
    //2. end = start 无法判断这个区间是不是有序
    //3. end < start 那么这个区间一定是旋转后的
    bool search(int* A, int n, int target) {
        // write code here
        int left = 0;
        int right = n - 1;
        while(left <= right) {
            int mid = (left + right) / 2;
            if(A[mid] == target) {
                return true;
            }
            if(A[left] < A[mid]) {
                if(A[left] <= target && target < A[mid]){
                    right = mid - 1;
                }else {
                    left = mid + 1;
                }
            }else if (A[mid] < A[right]) {
                if(A[mid] < target && target <= A[right]){
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }else {
                left++;
            }
        }
        return false;
    }
};
```
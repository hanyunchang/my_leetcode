```
三色快排问题

#include <exception>
class Solution {
public:
    void sortColors(int A[], int n) {
        int red_index = -1;
        int blue_index = n;
        int current_index = 0;
        while(current_index < blue_index) {
            if(A[current_index] == 0) { //红 
                //注意在current_index和red_index之间只可能是白色,因为其他颜色肯定会被交换出去。这个是关键点
                A[current_index] = A[red_index + 1];
                A[red_index + 1] = 0;
                current_index++;
                red_index++;
            }else if(A[current_index] == 1) {//白
                current_index++;
            }else {//蓝
                A[current_index] = A[blue_index - 1];
                A[blue_index - 1] = 2;
                blue_index--;
            }
        }
    }
};
```

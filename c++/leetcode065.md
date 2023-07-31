```
class Solution {
public:
    /**
     * 
     * @param height int整型vector 
     * @return int整型
     */
    //真正的解, 他的高度一定等于所在点集中高度最小的点的高度。这个由反正法可以证明。
    //那么我们只需要遍历所有的点，将其高度作为最大高度，来求矩形面积。遍历这些结果集即可。
    int largestRectangleArea(vector<int>& height) {
        // write code here
        int res = 0;
        for(int i = 0; i < height.size(); i++) {
            int h = height[i];
            int back_index = i + 1;
            int front_index = i - 1;
            while(front_index >= 0 && height[front_index] >= h) {
                front_index--;
            }
            while(back_index < height.size() && height[back_index] >= h) {
                back_index++;
            }
            
            int w = back_index - front_index - 1;
            res = max(res, h * w);
        }
        return res;
    }

    
};
```
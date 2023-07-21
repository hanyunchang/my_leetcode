```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 *	TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 * };
 */
#include <climits>
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param root TreeNode类 
     * @return int整型
     */
    int maxPathSum(TreeNode* root) {
        // write code here
        int res = INT_MIN;
        DFS(root, &res);
        return res;
    }
    /**
    * 对于每个子树的root节点, 我们取截止在root节点的最大path和穿过root节点的最大path，然后更新结果
    * 因为最大的path一定落在我们遍历的这个空间里
    */
    int DFS(TreeNode* node, int* res) {
        if(node == nullptr) {
            return 0;
        }
        int left_num = DFS(node->left, res);
        int right_num = DFS(node->right, res);

        *res =  max(*res, max(left_num + right_num + node->val, max(left_num, right_num) + node->val));
        *res = max(*res, node->val);

        return max(left_num, right_num) + node->val; 
    }
};
```
````
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */

#include <complex>
class Solution {
public:
    /**
     * 
     * @param root TreeNode类 
     * @return bool布尔型
     */
    bool isBalanced(TreeNode* root) {
        // write code here
        bool flag = true;
        DFS(root, flag);
        return flag;
    }

    int DFS(TreeNode* node, bool& flag) {
        if(node == nullptr) {
            return 0;
        }

        int left_height = DFS(node->left, flag);
        int right_height = DFS(node->right, flag);
        if(abs(left_height - right_height) >= 2) {
            flag = false;
        }
        return max(left_height, right_height) + 1;
    }
};
```
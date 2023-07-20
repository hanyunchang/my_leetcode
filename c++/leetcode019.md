```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 *	TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 * };
 */
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param root TreeNode类 
     * @return int整型
     */
    int sumNumbers(TreeNode* root) {
        // write code here
        if(root == nullptr) {
            return 0;
        }
        int res = 0;
        DFS(root, 0, &res);
        return res;
    }

    void DFS(TreeNode* node, int num, int* res) {
        int current_num = num * 10 + node->val;
        if(node->left == nullptr && node->right == nullptr){
            *res += current_num;
            return ;
        }

        if(node->left != nullptr){
            DFS(node->left, current_num, res);
        }

        if(node->right != nullptr) {
            DFS(node->right, current_num, res);
        }
    }
};

```
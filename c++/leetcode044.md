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
     * @param pRoot TreeNode类 
     * @return bool布尔型
     */
    bool isSymmetrical(TreeNode* pRoot) {
        // write code here
        if(pRoot == nullptr) {
            return true;
        }
        return isSymmetrical(pRoot->left, pRoot->right);
    }

    bool isSymmetrical(TreeNode* root1, TreeNode* root2) {
        if(root1 == nullptr && root2 == nullptr) {
            return true;
        }

        if(root1 == nullptr || root2 == nullptr) {
            return false;
        }

        if(root1->val != root2->val) {
            return false;
        }

        return isSymmetrical(root1->left, root2->right) && isSymmetrical(root1->right, root2->left);
    }

};
```
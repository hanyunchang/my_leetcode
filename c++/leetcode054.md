```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */

class Solution {
public:
    /**
     * 
     * @param root TreeNode类 
     * @return int整型vector
     */
    vector<int> inorderTraversal(TreeNode* root) {
        // write code here
        vector<int> res;

        stack<TreeNode*> stk;
        TreeNode* node = root;
        while(!stk.empty() || node != nullptr) {
            while(node != nullptr) {
                stk.push(node);
                node = node->left;
            }
            node = stk.top();
            stk.pop();
            res.push_back(node->val);//1. 这里保证，访问完本节点接下来一定是其右子节点
            node = node->right;//2. 这里如果为空，说明一个子树访问完了,下一步要访问的就是这个子树的节点了
        }
        return res;
    }
    //1、2保证了对于每个节点，都是先访问该节点的左子树的最后一个节点、该节点、该节点的右儿子这样的顺序
};


```
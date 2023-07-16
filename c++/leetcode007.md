/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */

#include <stack>
class Solution {
public:
    /**
     * 
     * @param root TreeNode类 
     * @return int整型vector
     */
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> vec;
        if(root == nullptr) {
            return vec;
        }
        stack<TreeNode*> stk;
        stk.push(root);
        while(!stk.empty()) {
            TreeNode* tmp = stk.top();
            stk.pop();
            vec.push_back(tmp->val);
            if(tmp->right != nullptr) {
                stk.push(tmp->right);
            }
            if(tmp->left != nullptr) {
                stk.push(tmp->left);
            }
        }
        return vec;
    }

    // vector<int> res;
    // vector<int> preorderTraversal(TreeNode* root) {
    //     // write code here
    //     if(root == nullptr) {
    //         return res;
    //     }
    //     res.push_back(root->val);
    //     preorderTraversal(root->left);
    //     preorderTraversal(root->right);
    //     return res;
    // }
};

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
     * @return bool布尔型
     */
    bool flag = true;
    bool isValidBST(TreeNode* root) {
        // write code here
        if(root == nullptr) {
            return true;
        }
        int dummy_value = INT_MIN;
        DFS(root, &dummy_value);
        return flag;
    }

    void DFS(TreeNode* node, int* prev_value) {//注意这里得是指针
        if(node->left != nullptr) {
            DFS(node->left, prev_value);
        }
        
        if(*prev_value >= node->val) {
           flag = false;  
        }
        
        *prev_value = node->val;
        if(node->right != nullptr) {
            DFS(node->right, prev_value);
        }
    }
};
```
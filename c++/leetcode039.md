```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */

#include <vector>
class Solution {
public:
    /**
     * 
     * @param inorder int整型vector 
     * @param postorder int整型vector 
     * @return TreeNode类
     */
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        // write code here
        if(inorder.size() == 0) {
            return nullptr;
        }
        int val = postorder[postorder.size() - 1];
        int index = 0;
        while(index < inorder.size()){
            if(inorder[index] == val){
                break;
            }
            index++;
        }

        int left_length = index;        
        vector<int> l_inorder(inorder.begin(), inorder.begin() + left_length);
        vector<int> r_inorder(inorder.begin() + left_length + 1, inorder.end());
        vector<int> l_postorder(postorder.begin(), postorder.begin() + left_length);
        vector<int> r_postorder(postorder.begin() + left_length, postorder.end() - 1);
     
        TreeNode* left = buildTree(l_inorder, l_postorder);
        TreeNode* right = buildTree(r_inorder, r_postorder);
        TreeNode* root = new TreeNode(val);
        root->left = left;
        root->right = right;
        return root;
    }
};
```
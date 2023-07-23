```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */

#include <algorithm>
class Solution {
public:
    /**
     * 
     * @param root TreeNode类 
     * @return int整型vector<vector<>>
     */
    vector<vector<int> > levelOrderBottom(TreeNode* root) {
        // write code here
        vector<vector<int>> res;
        if(root == nullptr) {
            return res;
        }

        queue<TreeNode*> que;
        que.push(root);
        while(!que.empty()) {
            int size = que.size();
            vector<int> tmp_vec;
            while(size > 0) {
                TreeNode* node = que.front();
                que.pop();

                tmp_vec.push_back(node->val);
                if(node->left != nullptr) {
                    que.push(node->left);
                }
                if(node->right != nullptr) {
                    que.push(node->right);
                }
                size--;
            }
            res.push_back(tmp_vec);
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```
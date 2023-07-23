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
     * @param n int整型 
     * @return TreeNode类vector
     */
    vector<TreeNode*> generateTrees(int n) {
        // write code here
        return _generateTree(1, n);
    }

    vector<TreeNode*> _generateTree(int start, int end){
        vector<TreeNode*> res;
        if(start > end) {
            res.push_back(nullptr);
            return res;
        }

        for(int var = start; var <= end; var++) {
            for(auto left : _generateTree(start, var - 1)){
                for(auto right : _generateTree(var + 1, end)){
                    auto root = new TreeNode(var);
                    root->left = left;
                    root->right = right;
                    res.push_back(root);
                }
            }
        }
        return res;
    }

};
```
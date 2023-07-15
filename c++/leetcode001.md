/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */

#include <algorithm>
#include <climits>
class Solution {
public:
    /**
     * 
     * @param root TreeNode类 
     * @return int整型
     */
    int run(TreeNode* root) {
        // write code here
        if(root == nullptr) {
            return 0;
        }
        return run_(root);
    }
    int run_(TreeNode* node){
        if(node == nullptr) {
            return INT_MAX;
        }
        if(node->left == nullptr && node->right == nullptr){
            return 1;
        }
        int l_min_length = run_(node->left);
        int r_min_length = run_(node->right);
        return std::min(l_min_length, r_min_length) + 1;
    }
};

* std::min在<algorithm>中
* INT_MAX在<climits>中

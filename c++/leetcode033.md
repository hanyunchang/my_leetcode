```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 *	TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 * };
 */
#include <vector>
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param root TreeNode类 
     * @param target int整型 
     * @return int整型vector<vector<>>
     */
    vector<vector<int> > FindPath(TreeNode* root, int target) {
        vector<vector<int>> res;
        
        if(root == nullptr) {
            return res;
        }
        vector<int> current_path;
        current_path.push_back(root->val);
        DFS(root, target, root->val, current_path, res);
        return res;
    }

    void DFS(TreeNode* node, int target, int current_num, vector<int>& current_path, vector<vector<int>>& res){
        if(node->left == nullptr && node->right == nullptr) {
            if(current_num == target) {
                res.push_back(current_path);
            }
            return ;
        }
        
        if(node->left != nullptr) {
            current_path.push_back(node->left->val);
            DFS(node->left, target, current_num + node->left->val, current_path, res);
            current_path.erase(current_path.end() - 1);
        }
        if(node->right != nullptr) {
            current_path.push_back(node->right->val);
            DFS(node->right, target, current_num + node->right->val, current_path, res);
            current_path.erase(current_path.end() - 1);            
        }
    }
};
```
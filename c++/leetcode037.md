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
     * @param nums int整型vector 
     * @return TreeNode类
     */
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        // write code here
        if(nums.size() == 0){
            return nullptr;
        }
        if(nums.size() == 1){
            return new TreeNode(nums[0]);
        }
        
        int middle_index = nums.size() / 2;
        vector<int> left_array(nums.begin(), nums.begin() + middle_index);
        vector<int> right_array(nums.begin() + middle_index + 1, nums.end());
        TreeNode* left = sortedArrayToBST(left_array);
        TreeNode* right = sortedArrayToBST(right_array);
        TreeNode* root = new TreeNode(nums[middle_index]);
        root->left = left;
        root->right = right;
        return root;
    }
};
```

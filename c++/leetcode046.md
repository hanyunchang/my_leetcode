```
/**
 * Definition for binary tree
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:

    int* first = nullptr;
    int* second = nullptr;
    void recoverTree(TreeNode *root) {
        if(root == nullptr) {
            return ;
        }
        int dummy_value = INT_MIN;//链表的第一个元素的前面的值设置为INT_MIN
        int* prev_value = &dummy_value;
        DFS(root, &prev_value);

        int tmp = *first;
        *first = *second;
        *second = tmp;
    }

    void DFS(TreeNode* node, int** prev_value) {//注意这里要是二维指针
        if(node->left != nullptr) {
            DFS(node->left, prev_value);
        }
        
        if(node->val < **prev_value) {
            if(first == nullptr) {
                first = *prev_value;
                second = &(node->val);
            }else {
                second = &(node->val);
            }
        }

        *prev_value = &(node->val);
        if(node->right != nullptr) {
            DFS(node->right, prev_value);
        }
    }
};
```
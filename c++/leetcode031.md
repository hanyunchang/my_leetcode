```
/**
 * Definition for binary tree with next pointer.
 * struct TreeLinkNode {
 *  int val;
 *  TreeLinkNode *left, *right, *next;
 *  TreeLinkNode(int x) : val(x), left(NULL), right(NULL), next(NULL) {}
 * };
 */
class Solution {
public:
    void connect(TreeLinkNode *root) {
        if(root == nullptr) {
            return ;
        }
        TreeLinkNode* prev_head = root;
        while(prev_head->left != nullptr) {
            TreeLinkNode* prev_current = prev_head;
            while(prev_current != nullptr && prev_current->left != nullptr) {
                prev_current->left->next = prev_current->right;
                if(prev_current->next != nullptr) {
                    prev_current->right->next = prev_current->next->left;
                }
                prev_current = prev_current->next;
            }
            prev_head = prev_head->left;
        }
    }
};
```
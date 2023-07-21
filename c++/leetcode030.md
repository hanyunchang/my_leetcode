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
        while(prev_head != nullptr) {
            TreeLinkNode dummy(-1);
            TreeLinkNode* current = &dummy;
            TreeLinkNode* prev_current = prev_head;
            while(prev_current != nullptr) {
                if(prev_current->left != nullptr) {
                    current->next = prev_current->left;
                    current = current->next;
                }
                if(prev_current->right != nullptr) {
                    current->next = prev_current->right;
                    current = current->next;
                }
                prev_current = prev_current->next;
            }
            prev_head = dummy.next;
        }
    }
};
```
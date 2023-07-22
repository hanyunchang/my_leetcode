```
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 */
/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 * };
 */

class Solution {
public:
    /**
     * 
     * @param head ListNode类 
     * @return TreeNode类
     */
    TreeNode* sortedListToBST(ListNode* head) {
        // write code here
        if(head == nullptr) {
            return nullptr;
        }
        if(head->next == nullptr) { // 注意这一步
            return new TreeNode(head->val);
        }

        ListNode* first = head;
        ListNode* slow = head;
        ListNode* slow_prev = nullptr;
        while(first != nullptr && first->next != nullptr) {
            slow_prev = slow;
            slow = slow->next;
            first = first->next->next;
        }

        if(slow_prev != nullptr){
            slow_prev->next = nullptr;
        }

        TreeNode* left = sortedListToBST(head);
        TreeNode* right = sortedListToBST(slow->next);

        TreeNode* root = new TreeNode(slow->val);
        root->left = left;
        root->right = right;
        return root;
    }

};
```

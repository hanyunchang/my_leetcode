/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 * };
 */

#include <cstdio>
class Solution {
public:
    /**
     * 
     * @param head ListNode类 
     * @return ListNode类
     */
    ListNode* gb(ListNode* left, ListNode* right){
        ListNode dummy(-1);
        ListNode* current = &dummy;
        while(left != nullptr && right != nullptr){
            if(left->val < right->val){
                current->next = left;
                left = left->next;
            }else{
                current->next = right;
                right = right->next;
            }
            current = current->next;
        }
        current->next = (left == nullptr ? right : left);
        return dummy.next;
    }

    ListNode* sortList(ListNode* head) {
        if(head == nullptr || head->next == nullptr){
            return head;
        }
        ListNode* slow = head;
        ListNode* fast = head->next;
        while(fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* right = slow->next;
        slow->next = nullptr;
        return gb(sortList(head), sortList(right));
    }
};
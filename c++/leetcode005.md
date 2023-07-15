/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 * };
 */

#include <bits/types/struct_tm.h>
class Solution {
public:
    /**
     * 
     * @param head ListNode类 
     * @return ListNode类
     */
    ListNode* insertionSortList(ListNode* head) {
        // write code here
        if(head == nullptr || head->next == nullptr){
            return head;
        }
        insertionSortList(head->next);
        ListNode* prev = head;
        ListNode* current = head->next;
        while(current != nullptr && prev->val > current->val){
            int tmp = current->val;
            current->val = prev->val;
            prev->val = tmp;
            prev = current;
            current = current->next;
        }
        return head;
    }
};
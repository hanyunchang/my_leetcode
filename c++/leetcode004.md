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
        ListNode* slow_prev = nullptr;
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast != nullptr && fast->next != nullptr) {
            slow_prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* right = slow_prev->next;
        slow_prev->next = nullptr;
        return gb(sortList(head), sortList(right));
    }
};



---------
* 快慢指针写法的范式
        if(head == nullptr || head->next == nullptr){
            return head;
        }
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }

这样slow最终落在[ n / 2 ]的下标处，我们只要记住这一种写法就行了。比如我们想拿到[ n / 2 ] - 1 的下标
那就这样写
        if(head == nullptr || head->next == nullptr){
            return head;
        }
        ListNode* slow_prev = nullptr;
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast != nullptr && fast->next != nullptr) {
            slow_prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }

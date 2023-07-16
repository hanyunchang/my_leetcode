/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void reorderList(ListNode *head) {
        if(head == nullptr || head->next == nullptr) {
            return ;
        }
        ListNode* middle = get_middle(head);
        ListNode* right_head = reverse(middle->next);
        middle->next = nullptr;
        merge(head, right_head);
    }
    ListNode* get_middle(ListNode* head){
        if(head == nullptr || head->next == nullptr) {
            return head;
        }
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;
    }
    ListNode* reverse(ListNode* head){
        ListNode dummy(-1);
        while(head != nullptr){
            ListNode* node = head;
            head = head->next;
            node->next = dummy.next;
            dummy.next = node;
        }
        return dummy.next;
    }
    ListNode* merge(ListNode* left_head, ListNode* right_head){
        if(left_head == nullptr || right_head == nullptr){
            return left_head == nullptr ? right_head : left_head;
        }
        left_head->next = merge(right_head, left_head->next);
        return left_head;
    }

};

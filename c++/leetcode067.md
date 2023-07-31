```
/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 *	ListNode(int x) : val(x), next(nullptr) {}
 * };
 */
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param head ListNode类 
     * @return ListNode类
     */
    ListNode* deleteDuplicates(ListNode* head) {
        // write code here
        if(head == nullptr){
            return nullptr;
        }

        ListNode dummy(-1);
        ListNode* tail_of_new_list = &dummy;
        ListNode* current = head;
        while(current != nullptr) {
            //如果处于重复的链表段，一直往下走到最后一个值
            while(current->next != nullptr && current->val == current->next->val) {
                    current = current->next;
            }
            
            //将current这个节点摘出来
            ListNode* tmp = current;
            current = current->next;
            tmp->next = nullptr;

            tail_of_new_list->next = tmp;
            tail_of_new_list = tail_of_new_list->next;
        } 
        return dummy.next;
    }
};
```
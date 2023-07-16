```c++

/*
struct ListNode {
    int val;
    struct ListNode *next;
    ListNode(int x) :
        val(x), next(NULL) {
    }
};
*/
class Solution {
public:
    ListNode* EntryNodeOfLoop(ListNode* pHead) {
         if(pHead == nullptr){
            return pHead;
         }
         ListNode* slow = pHead;
         ListNode* fast = pHead;
         while(fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
            if(slow == fast) {
                return get_entrance(pHead, fast);
            }
         }
         return nullptr;
    }
    ListNode* get_entrance(ListNode* slow, ListNode* fast){
        while(fast != slow){
            slow = slow->next;
            fast = fast->next;
        }
        return slow;
    }
};

```
原理见： https://blog.csdn.net/qq_41634872/article/details/105744052?ops_request_misc=&request_id=88ccbb96b71340a991877f4269d64d2a&biz_id=&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~koosearch~default-1-105744052-null-null.268^v1^control&utm_term=%E5%BF%AB%E6%85%A2&spm=1018.2226.3001.4450

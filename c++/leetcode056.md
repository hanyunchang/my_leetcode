* 解法一
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
     * @param m int整型 
     * @param n int整型 
     * @return ListNode类
     */
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        // write code here
        ListNode dummy(-1);
        dummy.next = head;

        //找第m个节点的prev和第 n个节点
        ListNode* m_prev_node = &dummy;
        while((m - 1) > 0) {
            m_prev_node = m_prev_node->next;
            m--;
        }
        
        ListNode* n_node = &dummy;
        while(n > 0) {
            n_node = n_node->next;
            n--;
        }
        
        ListNode* n_succeed_node = n_node->next;
        n_node->next = nullptr;
        ListNode* tmp = m_prev_node->next;
        m_prev_node->next = nullptr;
        while(tmp != nullptr) {
            ListNode* next = m_prev_node->next;
            ListNode* tmp_next = tmp->next;
            m_prev_node->next = tmp;
            tmp->next = next;

            tmp = tmp_next;
        }

        ListNode* current = &dummy;
        while(current->next != nullptr) {
            current = current->next;
        }
        current->next = n_succeed_node;

        return dummy.next;
    }



};
```
* 解法二(jav的代码，懒得改了)
```
    public ListNode reverseBetween(ListNode head, int m, int n) {
        ListNode Head=new ListNode(-1);
        Head.next=head;
        ListNode StartPre=Head;
        for(int i=1;i<m;i++) StartPre=StartPre.next;//刚开始这里用while循环，直接对m--,造成了bug
        ListNode end=StartPre.next;//我刚一开始尝试让end的初始值为StartPre 它的坏处是end会操作StartPre与StartPre本身的功能相互干扰
        for(int i=1;i<=n-m;i++){   //改进后，让end的初始值为第一个被交换的节点，最终这个节点将成为反转链表的最后一个节点，也符合end的语义
            ListNode tmp=end.next;
            end.next=end.next.next;
            tmp.next=StartPre.next;
            StartPre.next=tmp;
        }
        return Head.next;
    }
```

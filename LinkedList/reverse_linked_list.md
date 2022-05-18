[Question Link](https://leetcode.com/problems/reverse-linked-list/)

```
class Solution {
public:
    ListNode* reverseList(ListNode* &head) {
        /*

        // Iterative solution:

        // case when there is no node or single node.
        if(head == NULL || head->next == NULL) return head;

        ListNode* ptr1 = head;
        ListNode* ptr2 = ptr1->next;
        ListNode* ptr3 = NULL;
        head->next = NULL;

        if(ptr2) ptr3 = ptr2->next;
        while(ptr2){
            ptr2->next = ptr1;
            ptr1 = ptr2;
            ptr2 = ptr3;
            if(ptr3) ptr3 = ptr3->next;
        }
        return ptr1;
        */

        // Recursive solution

        // Base case
        if(head == NULL or head->next == NULL) return head;

        ListNode* newHead = reverseList(head->next);
        head->next->next = head;
        head->next = NULL;

        return newHead;
    }
};
```

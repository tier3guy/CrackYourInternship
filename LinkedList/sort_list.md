[Question Link](https://leetcode.com/problems/sort-list/)

```
class Solution {
public:
    ListNode* sortList(ListNode* head) {

        /* My approach to apply merge sort recursively and to use the stack space to solve the problem. */

        /* Case when there is no node or only one node in the list */
        if(!head or !head->next) return head;

        /* Lets find the mid */
        ListNode* slow = head;
        ListNode* fast = head;

        while(fast and fast->next and fast->next->next){
            slow = slow->next;
            fast = fast->next->next;
        }/* after the loop overs the slow pointer is pointing to the first mid */

        ListNode* l1 = head; ListNode* l2 = slow->next;
        slow->next = nullptr;


        l1 = sortList(l1);
        l2 = sortList(l2);

        head = (l1->val <= l2->val)? l1 : l2;
        slow = head; /* Lets reuse slow pointer */

        while(l1 and l2){
            if(l1->val <= l2->val){

                while(l1 and l1->next and l1->next->val <= l2->val) l1 = l1->next;
                slow = l1->next;
                l1->next = l2;
                l1 = slow;
            }
            else{
                while(l2 and l2->next and l2->next->val < l1->val) l2 = l2->next;
                slow = l2->next;
                l2->next = l1;
                l2 = slow;
            }
        }

        return head;
    }
};
```

[Question Link](https://leetcode.com/problems/reorder-list/)

```
class Solution {

    ListNode* getMid(ListNode* head){

        if(head == nullptr or head->next == nullptr) return head;

        ListNode* slow = head;
        ListNode* fast = head;
        ListNode* helper = nullptr;

        while(fast and fast->next){
            fast = fast->next->next;
            helper = slow;
            slow = slow->next;
        }
        helper->next = nullptr;
        return slow;
    }

    ListNode* reverse(ListNode* head){

        if(head == nullptr or head->next == nullptr) return head;

        ListNode* ptr1 = head;
        ListNode* ptr2 = ptr1->next;
        ListNode* ptr3 = ptr2->next;

        while(ptr2){
            ptr2->next = ptr1;
            ptr1 = ptr2;
            ptr2 = ptr3;

            if(ptr3) ptr3 = ptr3->next;
        }

        head->next = nullptr;

        return ptr1;
    }

public:
    void reorderList(ListNode* head) {

        // case when there are only zero, one or two nodes, no need to rearrange just return.
        if(head == NULL or head->next == NULL or head->next->next == NULL) return;

        /*
            // My Approach - but not a good one

            ListNode* ptr = head->next;
            ListNode* holder = head->next;
            while(ptr->next->next) ptr = ptr->next;

            head->next = ptr->next;
            ptr->next = NULL;
            head->next->next = holder;
            reorderList(holder);
        */

        /* Approach 2 - Learned from internet */

        ListNode* l1 = head;
        ListNode* l2 = reverse(getMid(head));

        ListNode* helper = head;
        while(helper){
            helper = l1->next;
            l1->next = l2;
            l1 = l2;
            l2 = helper;
        }

    }
};
```

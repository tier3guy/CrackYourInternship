[Question Link](https://leetcode.com/problems/palindrome-linked-list/)

```
class Solution {

private:

    ListNode* reverse(ListNode* head){

        if(head == nullptr or head->next == nullptr) return head;

        ListNode* ptr1 = head;
        ListNode* ptr2 = head->next;
        ListNode* ptr3 = head->next->next;

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
    bool isPalindrome(ListNode* head) {

        if(head == nullptr or head->next == nullptr) return true;

        // O(1) Space approach

        // finding the mid
        ListNode* slow = head;
        ListNode* fast = head;

        while(fast->next and fast->next->next){
            slow = slow->next;
            fast = fast->next->next;
        } /* now slow is at the first mid */

        slow->next = reverse(slow->next);
        fast = slow->next;
        slow = head;

        while(fast){

            if(slow->val != fast->val) return false;
            slow = slow->next;
            fast = fast->next;
        }

        return true;
    }
};
```

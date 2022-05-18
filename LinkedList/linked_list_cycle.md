[Question Link](https://leetcode.com/problems/linked-list-cycle/)

```
class Solution {
public:
    bool hasCycle(ListNode *head) {

        ListNode* fast = head;
        ListNode* slow = head;

        while(fast and fast->next){
            fast = fast->next->next;
            slow = slow->next;

            if(fast == slow) return true;
        }
        return false;
    }
};
```

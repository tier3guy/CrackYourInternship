[Question Link](https://leetcode.com/problems/remove-linked-list-elements/)

```
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {

        if(!head) return NULL;

        ListNode* temp = head;

        while(temp and temp->next){

            if(temp->next->val == val){
                temp->next = temp->next->next;
                // temp = temp->next;
            }
            else temp = temp->next;

        }

        if(head->val == val) return head->next;
        return head;
    }
};
```

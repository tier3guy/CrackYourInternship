[Question Link](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

```
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* temp = head;

        if(temp == NULL)
            return NULL;

        if(temp->next == NULL)
            return head;


        while(temp != NULL && temp->next != NULL){
            if(temp->val == temp->next->val){
                ListNode* todelete = temp->next;

                temp->next = temp->next->next;
                delete todelete;
            }
            else{
                temp = temp->next;
            }
        }


        return head;
    }
};
```

[Question Link](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

```
class Solution {

public:
    ListNode* deleteDuplicates(ListNode* head) {

        if(!head or !head->next) return head;

        ListNode* dummyHead = new ListNode(-105); dummyHead->next = head;

        ListNode* temp = head;
        while(temp and temp->next) temp = temp->next;
        temp->next = new ListNode(105);

        temp = head;
        ListNode* prev = dummyHead;
        ListNode* NEXT = head->next;

        ListNode* HEAD = nullptr;
        ListNode* LAST = HEAD;

        while(NEXT){

            if(temp->val > prev->val and temp->val < NEXT->val){

                temp->next = nullptr;

                if(HEAD){
                    LAST->next = temp;
                    LAST = temp;
                }
                else{
                    HEAD = temp;
                    LAST = HEAD;
                }

            }
            prev = temp;
            temp = NEXT;
            NEXT = NEXT->next;

        }

        return HEAD;
    }
};
```

[Question Link](https://leetcode.com/problems/intersection-of-two-linked-lists/)

```
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        int len1 = 0 , len2 = 0;
        ListNode* temp = headA;
        while(temp != NULL){
            len1++;
            temp = temp->next;
        }
        temp = headB;
        while(temp != NULL){
            len2++;
            temp = temp->next;
        }

        int diff = abs(len1 - len2);
        temp = headA;
        ListNode* temp1 = headB;

        if(len1 > len2){
            while(diff--){
                temp = temp->next;
            }
        }
        else{
            while(diff--){
                temp1 = temp1->next;
            }
        }
        int ans = 0;
        bool flag = false;
        while(temp != NULL){
            if(temp == temp1){
                return temp;
            }
            else{
                temp = temp->next;
                temp1 = temp1->next;
            }
        }

        return NULL;
    }
};
```

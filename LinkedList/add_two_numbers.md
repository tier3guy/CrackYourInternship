[Question Link](https://leetcode.com/problems/add-two-numbers/)

```
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int carry = 0;
        ListNode* ans = NULL; ListNode* temp = ans;

        while(l1 and l2){
            int sum = (l1->val + l2->val + carry)%10;
            carry = (l1->val + l2->val + carry)/10;

            if(ans == nullptr){
                ans = new ListNode(sum);
                temp = ans;
            }
            else{
                temp->next = new ListNode(sum);
                temp = temp->next;
            }
            l1 = l1->next;
            l2 = l2->next;
        }

        while(l1){
            int sum = (l1->val + carry)%10;
            carry = (l1->val + carry)/10;

            if(ans == nullptr){
                ans = new ListNode(sum);
                temp = ans;
            }
            else{
                temp->next = new ListNode(sum);
                temp = temp->next;
            }
            l1 = l1->next;
        }

        while(l2){
            int sum = (l2->val + carry)%10;
            carry = (l2->val + carry)/10;

            if(ans == nullptr){
                ans = new ListNode(sum);
                temp = ans;
            }
            else{
                temp->next = new ListNode(sum);
                temp = temp->next;
            }
            l2 = l2->next;
        }

        if(carry != 0){
            if(ans == nullptr){
                ans = new ListNode(carry);
                temp = ans;
            }
            else{
                temp->next = new ListNode(carry);
                temp = temp->next;
            }
        }

        return ans;
    }
};
```

[Question Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

```
class Solution {
private:
    int getLength(ListNode* head){

    int len = 0;

    ListNode* temp = head;
    while(temp){
        len += 1;
        temp = temp->next;
    }

    return len;
}
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {

        if(!head) return head;

        int len = getLength(head);

        if(n == len) return head->next;

        // nth node from the first means (length -n)th node from the start.
        n = len-n+1;

        ListNode* temp = head;

        while(n > 2){
            temp = temp->next;
            n -= 1;
        }

        temp->next = (temp->next)? temp->next->next : nullptr ;
        return head;

    }
};
```

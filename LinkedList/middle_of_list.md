[Question Link](https://leetcode.com/problems/middle-of-the-linked-list/)

```

class Solution {

    int getLength(ListNode* head){

        int _len = 0;
        while(head){
            _len += 1;
            head = head->next;
        }

        return _len;
    }

public:
    ListNode* middleNode(ListNode* head) {

        if(!head or !head->next) return head;

        int n = getLength(head)/2;

        while(--n){
            head = head->next;
        }

        return head->next;

    }
};
```

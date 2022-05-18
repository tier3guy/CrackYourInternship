[Question Link](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)

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
    int getDecimalValue(ListNode* head) {

        int n = getLength(head) - 1;

        int integerValue = 0;

        while(head){
            integerValue += (head->val * pow(2,n));
            n -= 1;
            head = head->next;
        }

        return integerValue;
    }
};
```

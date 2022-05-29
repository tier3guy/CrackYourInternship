[Question Link](https://leetcode.com/problems/add-two-numbers-ii/)

```
class Solution {
private:
    void addNode(ListNode* &head, int value){

        ListNode* node = new ListNode(value);
        node->next = head;
        head = node;
        return;
    }

public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {

        vector<int> v1, v2;
        ListNode* temp = l1;

        while(temp){
            v1.emplace_back(temp->val);
            temp = temp->next;
        }

        temp = l2;
        while(temp){
            v2.emplace_back(temp->val);
            temp = temp->next;
        }

        int i = v1.size()-1, j = v2.size()-1;

        ListNode* node = nullptr;
        int carry = 0, sum = 0;

        while(i >= 0 and j >= 0){
            sum = (carry + v1[i] + v2[j])%10;
            carry = (carry + v1[i] + v2[j])/10;
            addNode(node, sum);
            i--; j--;
        }

        while(i >= 0){
            sum = (carry + v1[i])%10;
            carry = (carry + v1[i])/10;
            addNode(node, sum);
            i--;
        }
        while(j >= 0){
            sum = (carry + v2[j])%10;
            carry = (carry + v2[j])/10;
            addNode(node, sum);
            j--;
        }

        if(carry != 0){
            addNode(node, carry);
        }

        return node;

    }
};
```

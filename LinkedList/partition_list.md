[Question Link](https://leetcode.com/problems/partition-list/)

```
class Solution {
private:
    void add_node(ListNode* &head, ListNode* &last, ListNode* node){

        node->next = nullptr;

        if(!head) head = node;
        else last->next = node;

        last = node;
    }
public:
    ListNode* partition(ListNode* head, int x) {

        if(!head) return head;

        ListNode* lesser = nullptr; ListNode* last_lesser = nullptr;
        ListNode* greater = nullptr; ListNode* last_greater = nullptr;

        ListNode* ptr = head;

        while(ptr){
            ListNode* node = ptr;
            ptr = ptr->next;
            if(node->val < x){
                add_node(lesser, last_lesser, node);
            }
            else{
                add_node(greater, last_greater, node);
            }
        }

        if(!last_lesser) return greater;

        last_lesser->next = greater;
        head = lesser;

        return head;
    }
};
```

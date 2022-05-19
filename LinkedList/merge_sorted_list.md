[Question Link](https://leetcode.com/problems/merge-two-sorted-lists)

```
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {

        if(list1 == nullptr) return list2;
        else if(list2 == nullptr) return list1;

        ListNode* ref = list1;
        ListNode* ptr1 = list1;
        ListNode* ptr2 = list2;

        while(ref and ptr1 and ptr2){
            if(ptr1->val <= ptr2->val){

                while(ptr1->next and ptr1->next->val <= ptr2->val) ptr1 = ptr1->next;

                ref = ptr1->next;
                ptr1->next = ptr2;
                ptr1 = ref;
            }
            else{

                while(ptr2->next and ptr2->next->val < ptr1->val) ptr2 = ptr2->next;

                ref = ptr2->next;
                ptr2->next = ptr1;
                ptr2 = ref;
            }
        }

        if(list1->val <= list2->val) return list1;
        return list2;
    }
};
```

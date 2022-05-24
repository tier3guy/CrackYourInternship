[Question Link](https://leetcode.com/problems/reverse-linked-list-ii/)

#### Left and right are given in the sence of index (starting from 1), it is not talking about the values of the nodes.

```
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {

        /* when there is no node or only one node, it makes no sense of reversing it, just return it */
        if(!head or !head->next) return head;

        /* creating one dummy nodes at the begining of the list to avoid if-else occurences */
        ListNode* dummyHead = new ListNode(-501); dummyHead->next = head;

        /* POINTERS THAT HELP US TO REVERSE THE LIST */
        ListNode* ptr1; ListNode* ptr2; ListNode* ptr3;

        ListNode* temp = dummyHead;
        ListNode* ref = nullptr;

        int counter = 0;

        while(temp and temp->next){

            /* storing the ref of the node just before the reversable part. */
            if(counter+1  == left and !ref){
                ref = temp;
                ptr1 = temp;
                ptr2 = temp->next;
                ptr3 = (ptr2) ? ptr2->next : nullptr;
            }

            if(ref){
                while(counter != right){
                    ptr2->next = ptr1;
                    ptr1 = ptr2;
                    ptr2 = ptr3;
                    if(ptr3) ptr3 = ptr3->next;
                    counter += 1;
                }

                ref->next->next = ptr2;
                ref->next = ptr1;

                if(left == 1) head = ptr1;

                break;
            }
            else{
                temp = temp->next;
                counter += 1;
            }
        }

        return head;
    }
};
```

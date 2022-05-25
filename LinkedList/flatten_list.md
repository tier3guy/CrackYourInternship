[Question Link](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)

```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* prev;
    Node* next;
    Node* child;
};
*/

class Solution {
public:
    Node* flatten(Node* head) {

        Node* ptr = head;

        /* Recuring all the sub-childs */
        while(ptr){
            if(ptr->child) flatten(ptr->child);
            ptr = ptr->next;
        }

        ptr = head;
        Node* NEXT = head;

        /* Merging child and the parent list iteratively */
        while(ptr){

            if(ptr->child){

                Node* temp = ptr;
                NEXT = ptr->next;
                ptr = ptr->child;

                while(ptr->next) ptr = ptr->next;

                ptr->next = NEXT;
                if(NEXT) NEXT->prev = ptr;

                temp->next = temp->child;
                temp->child->prev = temp;

                temp->child = NULL;

            }

            ptr = ptr->next;
        }

        return head;
    }
};
```

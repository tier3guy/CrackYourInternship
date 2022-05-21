[Question Link](https://practice.geeksforgeeks.org/problems/reverse-a-linked-list-in-groups-of-given-size/1)

```
class Solution
{
    public:
    struct node *reverse (struct node *head, int k)
    {
        // empty list or list with one node is always sorted, so just return it ...
        if(head == nullptr || head->next == nullptr) return head;


        // helper variables ...

        int window = k-1; // why -1 ? reason is between n node there will n-1 links that we have to update ...

        struct node* ptr1 = head;
        struct node* ptr2 = ptr1->next;
        struct node* ptr3 = ptr2->next;


        while(window and ptr2){
            ptr2->next = ptr1;
            ptr1 = ptr2;
            ptr2 = ptr3;

            if(ptr3) ptr3 = ptr3->next;

            window -= 1;
        }

        head->next = reverse(ptr2, k);

        return ptr1;
    }
};
```

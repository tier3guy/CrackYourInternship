[Question Link](https://practice.geeksforgeeks.org/problems/flattening-a-linked-list/1/)

```
Node *flatten(Node *root)
{


    // Recursive solution

    if(!root) return nullptr;

    Node* ptr2 = flatten(root->next);
    Node* ptr1 = root;

    Node* list_head = new Node(-1);
    Node* last = list_head;

    while(ptr1 && ptr2){

        if(ptr1->data <= ptr2->data){
            ptr1->next = nullptr;
            last->bottom = ptr1;
            ptr1 = ptr1->bottom;
        }
        else{
            ptr2->next = nullptr;
            last->bottom = ptr2;
            ptr2 = ptr2->bottom;
        }
        last = last->bottom;

    }

    if(ptr1) last->bottom = ptr1;
    else if(ptr2) last->bottom = ptr2;

    return list_head->bottom;



    // Iterative solution


}
```

[Question Link](https://practice.geeksforgeeks.org/problems/subtraction-in-linked-list/1/)

```
int count_node(Node* head){

    int count = 0;

    while(head){
        count += 1;
        head = head->next;
    }

    return count;
}

bool update_largest(Node* &l1, Node* &l2){

    int n1 = count_node(l1);
    int n2 = count_node(l2);

    Node* temp1 = l1;
    Node* temp2 = l2;

    bool equal = true;

    if(n1 == n2){
        Node* ptr1 = l1;
        Node* ptr2 = l2;

        while(ptr1 and ptr2){

            if(ptr1->data > ptr2->data){
                l1 = temp1;
                l2 = temp2;
                equal = false;
                break;
            }
            else if(ptr1->data < ptr2->data){
                l2 = temp1;
                l1 = temp2;
                equal = false;
                break;
            }
            ptr1 = ptr1->next;
            ptr2 = ptr2->next;

        }

        return equal;
    }

    if(n1 > n2){
        l1 = temp1;
        l2 = temp2;
    }
    else if(n2 > n1){
        l1 = temp2;
        l2 = temp1;
    }

    return false;

}

void reverse_list(Node* &head){

    if(!head || !head->next) return;

    Node* ptr1 = nullptr;
    Node* ptr2 = head;
    Node* ptr3 = head->next;

    while(ptr2){
        ptr2->next = ptr1;
        ptr1 = ptr2;
        ptr2 = ptr3;
        if(ptr3) ptr3 = ptr3->next;
    }

    head = ptr1;
    return;
}

Node* subLinkedList(Node* l1, Node* l2)
{
    if(!l1 && !l2) return nullptr;

    // the no. could start from 0 0 0 like 0235, so lets tackle this
    while(l1 && l1->data == 0) l1 = l1->next;
    while(l2 && l2->data == 0) l2 = l2->next;



    // first we have to confirm that we are subtracting smaller no. from bigger one
    if(update_largest(l1, l2)) return new Node(0); // return when (l1 == l2)

    // after upgrade_largest func it is confirmed that num(l1) > num(l2) i.e l1 - l2 -> +ve
    reverse_list(l1);
    reverse_list(l2);



    // main substraction logic starts from here.
    Node* dummy = new Node(-1);
    Node* last = dummy;

    Node* ptr1 = l1;
    Node* ptr2 = l2;

    while(ptr1 && ptr2){

        if(ptr1->data < 0){
            ptr1->data = ptr1->data + 10;
            if(ptr1->next) ptr1->next->data = ptr1->next->data - 1;
        }
        if(ptr1->data < ptr2->data){
            last->next = new Node((ptr1->data) - (ptr2->data) + 10);
            last = last->next;
            if(ptr1->next) ptr1->next->data = ptr1->next->data - 1;
        }
        else{
            last->next = new Node((ptr1->data - ptr2->data));
            last = last->next;
        }
        ptr1 = ptr1->next;
        ptr2 = ptr2->next;
    }

    if(ptr1) last->next = ptr1;

    while(ptr1){
        if(ptr1->data < 0){
            ptr1->data = ptr1->data + 10;
            if(ptr1->next) ptr1->next->data = ptr1->next->data - 1;
        }
        ptr1 = ptr1->next;
    }

    dummy = dummy->next;
    reverse_list(dummy);

    while(dummy && dummy->data == 0){
        dummy = dummy->next;
    }

    return dummy;
}
```

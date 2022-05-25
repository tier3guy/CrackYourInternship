[Question Link](https://practice.geeksforgeeks.org/problems/segregate-even-and-odd-nodes-in-a-linked-list5035/1)

```
class Solution{
public:
    Node* divide(int N, Node *head){

        Node* evenHead = new Node(-1); Node* evenTail = evenHead;
        Node* oddHead = new Node(-1); Node* oddTail = oddHead;

        Node* temp = head;
        while(temp){

            if(temp->data % 2 == 0){
                evenTail->next = temp;
                temp = temp->next;
                evenTail = evenTail->next;
                evenTail->next = nullptr;
            }
            else{
                oddTail->next = temp;
                temp = temp->next;
                oddTail = oddTail->next;
                oddTail->next = nullptr;
            }
        }
        evenTail->next = oddHead->next;

        return evenHead->next;
    }
};
```

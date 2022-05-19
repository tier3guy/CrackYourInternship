[Question Link](https://practice.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1#)

```
class Solution
{

    private:

    void joinList(Node* &head, Node* &last, Node* toJoin){

        if(!head){
            head = toJoin;
            last = head;
        }
        else{
            last->next = toJoin;
            last = toJoin;
        }
        last->next = nullptr;

    }

    public:

    Node* segregate(Node *head) {

        Node* zH = nullptr; Node* zT = nullptr;
        Node* oH = nullptr; Node* oT = nullptr;
        Node* tH = nullptr; Node* tT = nullptr;

        Node* temp = head;
        while(temp){
            Node* curr = temp;
            temp = temp->next;

            if(curr->data == 0){
                joinList(zH, zT, curr);
            }
            else if(curr->data == 1){
                joinList(oH, oT, curr);
            }
            else if(curr->data == 2){
                joinList(tH, tT, curr);
            }
        }

        if(zH){
            zT->next = (oH)? oH : tH;
        }
        if(oH) oT->next = tH;

        if(zH) return zH;
        if(oH) return oH;
        return tH;

    }
};

// we can remove all these if cases by creating three dummy nodes to resolve all the null cases.

```

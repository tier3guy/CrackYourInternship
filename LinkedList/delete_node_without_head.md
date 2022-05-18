[Question Link](https://practice.geeksforgeeks.org/problems/delete-without-head-pointer/1/#)

```
class Solution
{
    public:

    void deleteNode(Node *del)
    {
        Node* temp = del;
        while(temp->next){
            temp->data = temp->next->data;
            temp = temp->next;
        }
        temp = del;
        while(temp->next->next){
            temp = temp->next;
        }
        temp->next = nullptr;
    }

};
```

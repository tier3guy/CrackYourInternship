[Question Link](https://leetcode.com/problems/copy-list-with-random-pointer/)

```
class Solution {
private:

    unordered_map<Node*, Node*> analogous_of;

    void addNode(Node* &head, Node* &last, Node* node){

        Node* newNode = new Node(node->val);

        analogous_of[node] = newNode;

        if(head == nullptr){
            head = newNode;
            last = head;
            return;
        }
        last->next = newNode;
        last = last->next;
        return;

    }

public:
    Node* copyRandomList(Node* head) {

        if(!head) return head;

        // O(N) stack space solution.

        /*

        Node* Head = nullptr; Node* last = nullptr;
        Node* ptr = head;

        while(ptr){
            addNode(Head, last, ptr);
            ptr = ptr->next;
        }

        ptr = head;

        while(ptr){
            Node* temp = analogous_of[ptr];

            if(ptr->random == nullptr) temp->random = nullptr;
            else temp->random = analogous_of[ptr->random];

            ptr = ptr->next;
        }

        return Head;

        */

        // O(1) space solution.

        Node* ptr = head;

        while(ptr){
            Node* node = new Node(ptr->val);
            node->next = ptr->next;
            ptr->next = node;

            ptr = node->next;
        }

        ptr = head;

        while(ptr){
            if(ptr->random == nullptr) ptr->next->random = nullptr;
            else ptr->next->random = ptr->random->next;
            ptr = ptr->next->next;
        }

        Node* HEAD = head->next;

        ptr = head;
        Node* PTR = HEAD;

        while(ptr){
            ptr->next = PTR->next;
            if(PTR->next) PTR->next = PTR->next->next;

            ptr = ptr->next;
            PTR = PTR->next;
        }

        return HEAD;
    }
};
```

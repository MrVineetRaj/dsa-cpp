# Insertion at the tail of LL

Given the head of a singly linked list and an integer X, insert a node with value X at the tail of the linked list and return the head of the modified list.

The tail is the last node of the linked list.

```cpp
/*
Definition of singly linked list:
struct ListNode
{
    int val;
    ListNode *next;
    ListNode(int data1)
    {
        val = data1;
        next = NULL;
    }
    ListNode(int data1, ListNode *next1)
    {
        val = data1;
        next = next1;
    }
};
*/

class Solution {
public:
    ListNode* insertAtTail(ListNode* &head, int X) {
        if(head == NULL){
            return new ListNode(X,NULL);
        }

        ListNode* curr = head;

        while(curr->next != NULL){
            curr=curr->next;
        }

        ListNode* newTail = new ListNode(X,NULL);

        curr->next = newTail;

        return head;
    }
};
```

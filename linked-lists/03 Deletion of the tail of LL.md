# Deletion of the tail of LL

Given the head of a singly linked list, delete the tail of the linked list and return the head of the modified list.

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
    ListNode* deleteTail(ListNode* &head) {
        ListNode *curr = head;

        // edge case head is tail it self;
        if(curr->next == NULL or curr == NULL) return NULL;

        while(curr->next->next != NULL){
            curr = curr->next;
        }

        ListNode* tail = curr->next;
        curr->next = NULL;
        delete(tail);

        return head;
    }
};
```

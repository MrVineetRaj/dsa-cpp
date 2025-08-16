# Detect a loop in LL

Given the head of a singly linked list. Return true if a loop exists in the linked list or return false.

A loop exists in a linked list if some node in the list can be reached again by continuously following the next pointer.

Internally, pos is used to denote the index(0-based) of the node from where the loop starts. Note that pos is not passed as a parameter.

```cpp
/*
Definition of singly linked list:
struct ListNode
{
    int val;
    ListNode *next;
    ListNode()
    {
        val = 0;
        next = NULL;
    }
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
    bool hasCycle(ListNode *head) {
        if(head == NULL || head->next == NULL ) return false;
        ListNode* f = head->next;
        ListNode* s = head;

        while(f != NULL && f->next != NULL){
            if(f == s) return true;
            f= f->next->next;
            s=s->next;
        }

        return false;
    }
};
```

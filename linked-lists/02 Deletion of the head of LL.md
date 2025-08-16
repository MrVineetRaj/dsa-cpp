# Deletion of the head of LL

Given the head of a singly linked list, delete the head of the linked list and return the head of the modified list.

The head is the first node of the linked list.

Please note that this section might seem a bit difficult without prior knowledge on what linkedlist is, we will soon try to add basics concepts for your ease! If you know the concepts already please go ahead to give a shot to the problem. Cheers!


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
    ListNode* deleteHead(ListNode* &head) {
        ListNode* curr = head;
        head = curr->next;

        curr->next = NULL;

        free(curr);
        
        return head;
    }
};
```
# Find Middle of Linked List

Given the head of a singly Linked List, return the middle node of the Linked List.

If the Linked List has an even number of nodes, return the second middle one.

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
    ListNode* middleOfLinkedList(ListNode* head) {
        if (head->next == NULL) {
            return head;
        }

        ListNode* slow = head;
        ListNode* fast = head->next;

        while(fast != NULL && fast->next != NULL){
            fast=fast->next->next;
            slow=slow->next;
        }

        if(fast == NULL){
            return slow;
        }

        return slow->next;
    }
};
```

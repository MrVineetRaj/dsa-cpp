# Insertion before the value X in LL

Given the head of a singly linked list and two integers X and val, insert a node with value val before the node with value X in the linked list and return the head of the modified list.

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
    ListNode* insertBeforeX(ListNode* &head, int X, int val) {
        ListNode* newNode = new ListNode(val,NULL);
        if(head == NULL) return NULL;

        if(head->val == X) {
            newNode->next = head;
            return newNode;
        }

        ListNode* curr = head;

        while(curr->next != NULL){
            if(curr->next->val == X){
                newNode->next = curr->next;
                curr->next = newNode;
                break;
            }
            curr = curr->next;
        }

        return head;
    }
};
```

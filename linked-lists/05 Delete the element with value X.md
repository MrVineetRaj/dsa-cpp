# Delete the element with value X

Given the head of a singly linked list and an integer X, delete the node with value X and return the head of the modified list.

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
    ListNode* deleteNodeWithValueX(ListNode* &head, int X) {
        // question asks to delete first occurance of X
        if(head->val == X) return head->next;

        ListNode* prev = NULL;
        ListNode* curr = head;

        while(curr != NULL){
            if(curr->val == X){
                prev->next = curr->next;
                curr->next = NULL;
                delete(curr);
                break;
            }
            prev = curr;
            curr = curr->next;
        }

        return head;
    }
};
```

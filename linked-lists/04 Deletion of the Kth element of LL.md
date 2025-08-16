# Deletion of the Kth element of LL

Given the head of a singly linked list and an integer k, delete the kth node of the linked list and return the head of the modified list.

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
    ListNode* deleteKthNode(ListNode*& head, int k) {

        if (head == NULL) {
            return NULL;
        }

        if(k == 1) return head->next;
      ListNode* curr = head;
        ListNode* nextPtr = head->next;

        int currAt = 1;  // tracking index of current pointer

        while (nextPtr != NULL) {
            currAt+=1;
            if (currAt == k) {
                curr->next = nextPtr->next;
                nextPtr->next = NULL;
                delete (nextPtr);
                break;
            }
            curr = nextPtr;
            nextPtr = nextPtr->next;
        }

        return head;
    }
};
```

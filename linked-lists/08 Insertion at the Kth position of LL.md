# Insertion at the Kth position of LL

Given the head of a singly linked list and two integers X and K, insert a node with value X as the kth node of the linked list and return the head of the modified list.

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
    ListNode* insertAtKthPosition(ListNode* &head, int X, int K) {
        // 1 indexed Linked List
        ListNode* newNode = new ListNode(X,NULL);
        if(K == 1) {
            newNode->next = head;
            return newNode;
        }
        ListNode* curr = head;
        int currentNodeAt = 1;
        while(curr != NULL){
            currentNodeAt+=1;
            if(currentNodeAt == K){
                 newNode->next = curr->next;
                 curr->next = newNode;
                 break;
            }
            curr=curr->next;
        }

        return head;
    }
};
```

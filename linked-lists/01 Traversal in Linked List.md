# Traversal in Linked List

Given the head of a singly Linked List. Traverse the entire Linked List and return its elements in an array in the order of their appearance.

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
    vector<int> LLTraversal(ListNode *head) {
        ListNode *curr = head;

        vector<int> ans;
        // ans.pu
        while(curr != NULL){
            ans.push_back(curr->val);
            curr = curr->next;
        }

        return ans;
    }
};
```

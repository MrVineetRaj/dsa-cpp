# Clone a LL with random and next pointer

Given the head of a special linked list of n nodes where each node contains an additional pointer called 'random' which can point to any node in the list or null.

Construct a **deep copy** of the linked list where,

- n new nodes are created with corresponding values as original linked list.
- The random pointers point to the corresponding new nodes as per their arrangement in the original list.
- Return the head of the newly constructed linked list.

**Note**: For custom input, a n x 2 matrix is taken with each row having 2 values:**[ val, random_index]** where,

- **val**: an integer representing ListNode.val
- **random_index**: index of the node (0 - n-1) that the random pointer points to, otherwise -1.

```cpp
/*
Definition of singly linked list:
struct ListNode
{
    int val;
    ListNode *next;
    ListNode *random;
    ListNode()
    {
        val = 0;
        next = NULL;
        random = NULL;
    }
    ListNode(int data1)
    {
        val = data1;
        next = NULL;
        random = NULL;
    }
    ListNode(int data1, ListNode *next1, ListNode* r)
    {
        val = data1;
        next = next1;
        random = r;
    }
};
*/

class Solution {
   public:
    ListNode* copyRandomList(ListNode* head) {
        ListNode* temp = head;
        while (temp != NULL) {
            ListNode* newNode = new ListNode(temp->val);
            newNode->next = temp->next;
            temp->next = newNode;
            temp = temp->next->next;
        }

        // marking the random pointers
        temp = head;
        while (temp != NULL) {
            ListNode* newNode = temp->next;
            if (temp->random == NULL || temp->random->next == NULL) {
                newNode->random = NULL;
            } else {
                newNode->random = temp->random->next;
            }
            temp = temp->next->next;
        }

        // extracting the ans;
        temp = head;
        ListNode* ans = new ListNode(-1);

        ListNode* tAns = ans;
        while(temp != NULL ){
            tAns->next = temp->next;
            tAns = tAns->next;
            temp = temp->next->next;
        }

        return ans->next;
    }
};
```

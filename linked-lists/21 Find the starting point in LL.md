# Find the starting point in LL

Given the head of a singly linked list, the task is to find the starting point of a loop in the linked list if it exists. Return the starting node if a loop exists; otherwise, return null.

A loop exists in a linked list if some node in the list can be reached again by continuously following the next pointer. Internally, pos denotes the index (0-based) of the node from where the loop starts.

Note that pos is not passed as a parameter.

```cpp
class Solution {
public:
    ListNode* findStartingPoint(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;

        while (fast != NULL && fast->next != NULL) {

            slow = slow->next;
            fast = fast->next->next;

            if (slow == fast) {
                slow = head;

                while (slow != fast) {

                    slow = slow->next;
                    fast = fast->next;

                }

                return slow;
            }
        }

        //If no loop is found,
        //Return NULL
        return NULL;
    }
};
```

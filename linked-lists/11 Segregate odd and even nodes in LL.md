# Segregate odd and even nodes in LL

Given the head of a singly linked list. Group all the nodes with odd indices followed by all the nodes with even indices and return the reordered list.

Consider the 1st node to have index 1 and so on. The relative order of the elements inside the odd and even group must remain the same as the given input.

```cpp
class Solution {
public:
    // Function to rearrange nodes
    ListNode* oddEvenList(ListNode* head) {
        if (!head || !head->next)
            return head;

        /*Initialize pointers for odd
        and even nodes and keep
        track of the first even node*/
        ListNode* odd = head;
        ListNode* even = head->next;
        ListNode* firstEven = head->next;

        // Rearranging nodes
        while (even && even->next) {
            odd->next = odd->next->next;
            even->next = even->next->next;
            odd = odd->next;
            even = even->next;
        }

       /* Connect the last odd
       node to the first even node*/
        odd->next = firstEven;

        return head;
    }
};
```

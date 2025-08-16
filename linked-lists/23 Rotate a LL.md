# Rotate a LL

Given the head of a singly linked list containing integers, shift the elements of the linked list to the right by k places and return the head of the modified list. Do not change the values of the nodes, only change the links between nodes.

```cpp
class Solution {
public:

    ListNode* rotateRight(ListNode* head, int k) {
        if (head == nullptr || head->next == nullptr || k == 0)
            return head;

        // Calculating length
        ListNode* temp = head;
        int length = 1;
        while (temp->next != nullptr) {
            ++length;
            temp = temp->next;
        }

        // Link last node to first node
        temp->next = head;
        // When k is more than length of list
        k = k % length;
        // To get end of the list
        int end = length - k;
        while (end-- > 0)
            temp = temp->next;

        // Breaking last node link and pointing to NULL
        head = temp->next;
        temp->next = nullptr;

        return head;
    }
};
```

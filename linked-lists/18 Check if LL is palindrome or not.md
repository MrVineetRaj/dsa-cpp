# Check if LL is palindrome or not

Given the head of a singly linked list representing a positive integer number. Each node of the linked list represents a digit of the number, with the 1st node containing the leftmost digit of the number and so on. Check whether the linked list values form a palindrome or not. Return true if it forms a palindrome, otherwise, return false.

A palindrome is a sequence that reads the same forward and backwards.

```cpp
class Solution {
private:
    ListNode* reverseLinkedList(ListNode* head) {
        if (head == NULL || head->next == NULL) {
            return head;
        }

        ListNode* newHead = reverseLinkedList(head->next);

        ListNode* front = head->next;

        front->next = head;
        head->next = NULL;

        return newHead;
    }

public:
    bool isPalindrome(ListNode* head) {
        if (head == NULL || head->next == NULL) {
            return true;
        }

        ListNode* slow = head;
        ListNode* fast = head;

        while (fast->next != NULL && fast->next->next != NULL) {
            slow = slow->next;
            fast = fast->next->next;
        }

        ListNode* newHead = reverseLinkedList(slow->next);
        ListNode* first = head;
        ListNode* second = newHead;

        while (second != NULL) {
            if (first->val != second->val) {
                reverseLinkedList(newHead);
                return false;
            }

            first = first->next;

            // Move the second pointer
            second = second->next;
        }

        /*Reverse the second half
        back to its original state*/
        reverseLinkedList(newHead);

        // Linked List is a palindrome
        return true;
    }
};
```

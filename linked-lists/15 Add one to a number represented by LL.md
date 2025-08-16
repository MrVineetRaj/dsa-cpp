# Add one to a number represented by LL

Given the head of a singly linked list representing a positive integer number. Each node of the linked list represents a digit of the number, with the 1st node containing the leftmost digit of the number and so on. The task is to add one to the value represented by the linked list and return the head of a linked list containing the final value.

The number will contain no leading zeroes except when the value represented is zero itself.

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
private:
    ListNode *reverse(ListNode* head){
        ListNode* prev = NULL;
        ListNode* next = NULL;
        ListNode* curr = head;

        while(curr != NULL){
            next = curr->next;
            curr->next = prev ;
            prev = curr;
            curr = next;
        }

        return prev;
    }

public:
    ListNode *addOne(ListNode *head) {
        ListNode* temp = reverse(head);

        int carry = 1; // as we have to 1 assumed carray as 1 initally

        ListNode* curr = temp;

        while(curr != NULL){
            int sum = curr->val + carry;
            if(sum < 10){
                curr->val = sum;
                carry=0;
            }else{
                carry = sum/10;
                curr->val = sum%10;
            }
            curr=curr->next;
        }

        ListNode* ans = reverse(temp);

        if(carry != 0){
            ListNode* newNode = new ListNode(carry);
            newNode->next = ans;
            ans = newNode;
        }

        return ans;
    }
};
```

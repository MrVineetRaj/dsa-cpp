# Add two numbers in LL

Given two non-empty linked lists l1 and l2 which represent two non-negative integers.

The digits are stored in reverse order with each node storing one digit.

Add two numbers and return the sum as a linked list.

- The sum Linked List will be in reverse order as well.
- The Two given Linked Lists represent numbers without any leading zeros, except when the number is zero itself

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* curr1 = l1->next;
        ListNode* curr2 = l2->next;

        int firstSum = l1->val + l2->val;

        ListNode* l3 = new ListNode(firstSum%10,NULL);
        ListNode* sum = l3;
        int carry = firstSum/10;

        while(curr1 != NULL && curr2 != NULL){
            int nodeSum = curr1->val + curr2->val + carry;
            carry = nodeSum/10;
            nodeSum%=10;
            curr1=curr1->next;
            curr2=curr2->next;

            ListNode* newNode = new ListNode(nodeSum,NULL);
            sum->next = newNode;
            sum=sum->next;
        }


        while(curr1 != NULL){
            int nodeSum = curr1->val + carry;
            ListNode* newNode = new ListNode(nodeSum%10,NULL);
            sum->next = newNode;
            sum=sum->next;
            curr1=curr1->next;
            carry=nodeSum/10;
        }

        while(curr2 != NULL){
            int nodeSum =  curr2->val + carry;
            ListNode* newNode = new ListNode(nodeSum%10,NULL);
            sum->next = newNode;
            sum=sum->next;
            curr2=curr2->next;
            carry=nodeSum/10;
        }

        if(carry>0){
            ListNode* newNode = new ListNode(carry,NULL);
            sum->next = newNode;
        }


        return l3;
    }
};
```

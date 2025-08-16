# Merge two Sorted Lists

Given the heads of two linked lists, list1 and list2, where each linked list has its elements sorted in non-decreasing order, merge them into a single sorted linked list and return the head of the merged linked list.

```cpp
// Definition of singly linked list:
// struct ListNode
// {
//     int val;
//     ListNode *next;
//     ListNode(int data1)
//     {
//         val = data1;
//         next = NULL;
//     }
//     ListNode(int data1, ListNode *next1)
//     {
//         val = data1;
//         next = next1;
//     }
// };

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* ans = new ListNode(-1);
        ListNode* temp = ans;

        while(l1 != NULL && l2 != NULL){
            if(l1->val <= l2->val){
                temp->next = l1;
                temp = temp->next;
                l1=l1->next;
            }else{
                temp->next = l2;
                temp = temp->next;
                l2=l2->next;
            }
        }

        if(l1 != NULL){
            temp->next = l1;
        }
        if(l2 != NULL){
            temp->next = l2;
        }

        return ans->next;
    }
};
```

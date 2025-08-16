# Sort LL

Given the head of a singly linked list. Sort the values of the linked list in non-decreasing order and return the head of the modified linked list.

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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* ans = new ListNode(-1);
        ListNode* temp = ans;

        while (l1 != NULL && l2 != NULL) {
            if (l1->val <= l2->val) {
                temp->next = l1;
                temp = temp->next;
                l1 = l1->next;
            } else {
                temp->next = l2;
                temp = temp->next;
                l2 = l2->next;
            }
        }

        if (l1 != NULL) {
            temp->next = l1;
        }
        if (l2 != NULL) {
            temp->next = l2;
        }

        return ans->next;
    }

    ListNode* mergeSort(ListNode* h) {
        if(h == NULL || h->next == NULL) return h;
        ListNode* f = h;
        ListNode* s = h;

        while(f->next!=NULL && f->next->next!=NULL){
            f=f->next->next;
            s=s->next;
        }

        ListNode* h1 = h;
        ListNode* h2 = s->next;
        s->next=NULL;

        h1 = mergeSort(h1);
        h2 = mergeSort(h2);
        return mergeTwoLists(h1,h2);
    }

   public:
    ListNode* sortList(ListNode* head) {

        return mergeSort(head);;
    }
};
```

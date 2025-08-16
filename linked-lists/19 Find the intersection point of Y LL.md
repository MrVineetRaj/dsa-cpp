# Find the intersection point of Y LL

Given the heads of two linked lists A and B, containing positive integers. Find the node at which the two linked lists intersect. If they do intersect, return the node at which the intersection begins, otherwise return null.

The Linked List will not contain any cycles. The linked lists must retain their original structure, given as per the input, after the function returns.

**Note**: for custom input, the following parameters are required(your program is not provided with these parameters):

- **intersectVal** - The value of the node where the intersection occurs. This is -1 if there is no intersected node.
- **skipA** - The number of nodes to skip ahead in listA (starting from the head) to get to the intersected node(-1 if no intersection).
- **skipB** - The number of nodes to skip ahead in listB (starting from the head) to get to the intersected node(-1 if no intersection).
- **listA** - The first linked list.
- **listB** - The second linked list.

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

public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {

        if(headA == NULL || headB == NULL) return NULL;
        ListNode* t1 = headA;
        ListNode* t2 = headB;


        while(t1 != t2){
            t1=t1->next;
            t2=t2->next;

            if(t1 == t2) return t1;

            if(t1 == NULL) t1 = headB;
            if(t2 == NULL) t2 = headA;
        }

        return t1;
    }
};
```

# Reverse LL in group of given size K

Given the head of a singly linked list containing integers, reverse the nodes of the list in groups of k and return the head of the modified list. If the number of nodes is not a multiple of k, then the remaining nodes at the end should be kept as is and not reversed.

Do not change the values of the nodes, only change the links between nodes.

```cpp
class Solution {
public:
    ListNode* reverseLinkedList(ListNode *head)
    {

        ListNode* temp = head;
        ListNode* prev = NULL;

        while(temp != NULL){
            ListNode* front = temp->next;
            temp->next = prev;
            prev = temp;
            temp = front;
        }

        return prev;
    }

    ListNode* getKthNode(ListNode* temp, int k){
        k -= 1;
        // for k = 3;
        // iterations will be k = 2, k = 1; k = 0;

        while(temp != NULL && k > 0){
            k--;
            temp = temp -> next;
        }

        return temp;
    }

    ListNode* reverseKGroup(ListNode* head, int k){
        ListNode* temp = head;
        ListNode* prevLast = NULL;

        while(temp != NULL){
            ListNode* kThNode = getKthNode(temp, k);
            if(kThNode == NULL){
                if(prevLast){
                    prevLast -> next = temp;
                }
                break;
            }

            ListNode* nextNode = kThNode -> next;
            kThNode -> next = NULL;

            reverseLinkedList(temp);

            if(temp == head){
                head = kThNode;
            }else{
                prevLast -> next = kThNode;
            }

            prevLast = temp;

            temp = nextNode;
        }

        return head;
    }
};
```

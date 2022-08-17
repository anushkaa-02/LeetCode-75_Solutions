# Odd Even Linked List
- ## Question:
>Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.
>
>The first node is considered odd, and the second node is even, and so on.
>
>Note that the relative order inside both the even and odd groups should remain as it was in the input.
>
>You must solve the problem in O(1) extra space complexity and O(n) time complexity.

- Example :

      Input: head = [1,2,3,4,5]
      Output: [1,3,5,2,4]

- ## Solution:
```cpp
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        ListNode* n1=NULL;
        ListNode* n2=NULL;
        if(head==NULL or head->next==NULL) return head;
        ListNode* odd=head;
        ListNode* even=head->next;
        n1=odd;
        n2=even;
        while(odd!=NULL and even!=NULL)
        {
            if(even->next!=NULL)
            {
                odd->next=even->next;
                odd=even->next;
            }
            else 
            {
                odd->next=NULL;
                break;
            }
            if(odd->next!=NULL)
            {
                even->next=odd->next;
                even=odd->next;
            }
            else
            {
                even->next=NULL;
                break;
            }
               
        }
        ListNode* od=n1;
        while(n1->next!=NULL)
        {
            n1=n1->next;
        }
        n1->next=n2;
        return od;
    }
};
```
## Tags
`Linked List`

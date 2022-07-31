# Reversed Linked List
- ## Question:
>Given the head of a singly linked list, reverse the list, and return the reversed list.


- Example :

      Input: head = [1,2,3,4,5]
      Output: [5,4,3,2,1]
      
- ## Solution:
```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head==NULL or head->next==nullptr)//if only one node is present or zero node
            return head;
        ListNode* pre=NULL;
        ListNode* cur=head;
        ListNode* temp;
        while(cur!=NULL)
        {
            temp=cur->next;
            cur->next=pre;
            pre=cur;
            cur=temp;
        }
        return pre;
    }
};
```
## Tags
`Linked List` `Recursion`

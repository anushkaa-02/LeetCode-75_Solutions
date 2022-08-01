# Middle of the Linked List
- ## Question:
>Given the head of a singly linked list, return the middle node of the linked list.
>
>If there are two middle nodes, return the second middle node.

- Example :

      Input: head = [1,2,3,4,5]
      Output: [3,4,5]
      Explanation: The middle node of the list is node 3.
      
- ## Solution:
```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
    ListNode *temp,*cur;
    temp=cur=head;
    int count=1,mid;
    while(temp->next!=0){
        count++;
        temp=temp->next;
    }
    
    if(count%2==0){
        mid=ceil((count+1)/2);
    }
    else{
        mid=count/2;
    }
    
    while(mid--){
        cur=cur->next;
    }
    head=cur;
    return head;
}
};
```
## Tags
`Linked List` `Two Pointers`

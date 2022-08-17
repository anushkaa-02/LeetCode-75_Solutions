# Sort List
- ## Question:
>Given the head of a linked list, return the list after sorting it in ascending order.

- Example :

      Input: head = [-1,5,3,4,0]
      Output: [-1,0,3,4,5]

- ## Solution:
```cpp
class Solution {
public:
    void mergesorting(ListNode** head) 
    {
        ListNode* curr = *head; 
        ListNode* first; 
        ListNode* second; 
        if(curr == NULL || curr -> next == NULL)
            return;
        
        findmid(curr, &first,&second); 
        mergesorting(&first); 
        mergesorting(&second);
        
        *head = merge(first,second);
    }

    void findmid(ListNode* curr, ListNode** first, ListNode** second)
    {
        ListNode* slow = curr; 
        ListNode* fast = curr -> next;
        while(fast != NULL)
        {
            fast = fast -> next;
            if(fast != NULL)
            {
                fast = fast -> next;
                slow = slow -> next;
            }
        }
        
        *first = curr;
        *second = slow -> next; 
        slow -> next = NULL; 
    }
    ListNode* merge(ListNode* first, ListNode* second)
    {
        ListNode* answer = NULL; 
        
        if(first == NULL)
        {
            return second; 
        }
        
        if(second == NULL)
        {
            return first;
        }

        if(first -> val <= second -> val) 
        {
            answer = first;
            answer -> next = merge(first -> next, second); 
        }
        else
        {
            answer = second;
            answer -> next = merge(first, second -> next);
        }
        
        return answer; 
    }
    ListNode* sortList(ListNode* head) {
        mergesorting(&head); 
        
        return head;
    }
};
```

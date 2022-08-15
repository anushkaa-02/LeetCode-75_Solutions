# Palindrome Linked List
- ## Question:
>Given the head of a singly linked list, return true if it is a palindrome.


- Example :

      Input: head = [1,2,2,1]
      Output: true


- ## Solution:
```cpp
class Solution {
public:
    
    ListNode *midPoint(ListNode *head){
        
        if(!head) return NULL;

        ListNode* fast = head->next;
        ListNode* slow = head;

        while(fast != NULL && fast->next != NULL){
            fast = fast->next->next;
            slow = slow->next;
        }
        return slow;
    }
    
    ListNode* reverseLL(ListNode* &head){

        ListNode* prev = NULL;
        ListNode* curr = head;
        ListNode* next;

        while(curr != NULL){
            next = curr->next;
            curr->next = prev;

            prev = curr;
            curr = next;
        }

        return prev;
    }
    
    bool isPalindrome(ListNode* head) {
        
        ListNode* mid = midPoint(head);
        ListNode* rev = reverseLL(mid->next);
        
        while(rev){
            if(head->val != rev->val){
                return false;
            }rev = rev->next;
            head = head->next;
        }
        
        return true;
    }
};
```

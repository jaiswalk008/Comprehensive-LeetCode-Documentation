# [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) 

**This is the "Floyd's Cycle Detection Algorithm" or "Tortoise and Hare Algorithm".**
### Intuition :
The intuition behind the algorithm is that if there is a cycle in the linked list, 
then at some point during the traversal, the fast and slow pointers will be pointing to the same node.
The fast pointer moves twice as fast as the slow pointer, so if there is a cycle, **eventually** the fast pointer will "lap" the slow pointer and they will meet at the same node.

### Approach :
- In the code, we initialize two pointers, "slow" and "fast", to the head of the linked list. 
- We then start iterating through the list using a while loop that terminates when either "fast" reaches the end of the list (i.e., is NULL), or when "fast->next" reaches the end of the list. 
- During each iteration of the loop, we move the slow pointer one step forward, and the fast pointer two steps forward.
- If there is no cycle in the linked list, then eventually the fast pointer will reach the end of the list and the loop will terminate, returning false. 
- However, if there is a cycle, then the fast and slow pointers will **eventually** meet at the same node, and the loop will terminate early, returning true.

**Time Complexity:** O(N)

**Interative Approach**:
```
class Solution {
public:
    bool hasCycle(ListNode *head) {
        
        ListNode *slow = head, *fast=head;
        while(fast!=NULL && fast->next!=NULL){
            slow=slow->next;
            fast = fast->next->next;
            if(slow==fast) return true;
        }
        return false;
    }
};
```
**Recursive Approach**:
```
public:
    static bool cycle(ListNode *slow , ListNode *fast){
        if(fast==NULL || fast->next==NULL) return false;
        else if(slow==fast) return true;
        else{
            return cycle(slow->next,fast->next->next);
        }
    }
    bool hasCycle(ListNode *head) {
        
        if(head && head->next)return cycle(head->next,head->next->next);
        else return false;
    }
};
```

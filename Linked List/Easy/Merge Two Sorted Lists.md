# [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
### Approach:
The problem statement requires us to merge two sorted linked lists into a single sorted linked list. We can solve this problem by iterating over both input lists and comparing the node values at each step.

Here's the approach for the mergeTwoLists function:

- Initialize a pointer ans to NULL, which will point to the head of the merged list.
- If either list1 or list2 is empty, return the non-empty list as it is already sorted.
- Set pointers temp1 and temp2 to the head of list1 and list2, respectively.
- Set prev to NULL, which will keep track of the last node added to the merged list.
- Iterate over both lists until either temp1 or temp2 becomes NULL:
- If the value of temp1 is less than or equal to the value of temp2, add temp1 to the merged list and move temp1 to the next node of list1.
- Otherwise, add temp2 to the merged list and move temp2 to the next node of list2.
- Update the prev pointer to the node just added to the merged list.
- If there are any remaining nodes in list1 or list2, add them to the end of the merged list by setting prev->next to the remaining list.
- Finally, return the head of the merged list (ans).

**Code** :
#
```
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* ans=NULL;
        if(list1==NULL) return list2;
        else if(list2==NULL) return list1;

        else{
            ListNode* temp1 = list1;
            ListNode* temp2=list2;
            ListNode* prev = NULL;
            
            while(temp1!=NULL && temp2!=NULL){
                if(temp1->val<=temp2->val){
                    if(prev==NULL) {
                        prev = temp1;
                        ans= temp1;
                    }
                    else{
                        prev->next = temp1;
                        prev = temp1;
                    }
                    temp1= temp1->next;
                }
                else{
                    if(prev==NULL) {
                        prev = temp2;
                        ans= temp2;
                    }
                    else{
                        prev->next = temp2;
                        prev = temp2;
                    }
                    temp2 = temp2->next;
                }
            }
            if(temp1==NULL) prev->next = temp2;
            else prev->next = temp1;
        }
        return ans;
    }
};
```

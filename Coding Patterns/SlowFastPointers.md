# Interview_guide
FAAMG
The following is to find a cycle in a linked list.
This pattern is also known as tortoise and hare.
```
bool hasCycle(ListNode *head) {
if(head){
ListNode* slow = head;
ListNode* fast = (head->next) ? head->next->next : nullptr;

while((fast && fast->next) && slow != fast){
slow = slow->next;
fast = fast->next->next;
}

return (fast && fast->val == slow->val) ? true : false;
}

return false;
}
```

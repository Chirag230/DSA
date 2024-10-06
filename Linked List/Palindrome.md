2 APPROACH 
1.BEST APPROACH WITH MANIPULATING LL
 bool isPalindrome(ListNode* head) 
    {
        if(head->next==NULL)
        return true;
        ListNode*slow=head;
        ListNode*fast=head;
        ListNode*prev=NULL;
        while(fast!=NULL && fast->next!=NULL)
        {
            fast=fast->next->next;
            ListNode*store=slow->next;
            slow->next=prev;
            prev=slow;
            slow=store;
        }
        if(fast!=NULL)
        {
            slow=slow->next;
        }
        while(prev!=NULL && slow!=NULL)
        {
            if(prev->val==slow->val)
            {
                prev=prev->next;
                slow=slow->next;
            }
            else
            {
                return false;
            }
        }
        return true;
    }
2.WITHOUT CHANGING THE STRUCTURE OF LINKED LIST
class Solution {
public:
    ListNode*curr;
    bool solve(ListNode*head)
    {
        if(head==NULL)
        return true;
        bool ans = solve(head->next);
        if(curr->val!=head->val)
        {
            return false;
        }
        curr=curr->next;
        return ans;
    }
    bool isPalindrome(ListNode* head) 
    {

        if(head==NULL)
        return true;
        curr=head;
        return solve(head);
    }
};
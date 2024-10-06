class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) 
    {
        stack<ListNode*>s1;
        stack<ListNode*>s2;
        ListNode*temp1=headA;
        ListNode*temp2=headB;
        while(temp1!=NULL)
        {
            s1.push(temp1);
            temp1=temp1->next;
        }
        while(temp2!=NULL)
        {
            s2.push(temp2);
            temp2=temp2->next;
        }
        ListNode*ans=NULL;
        while(!s1.empty() && !s2.empty())
        {
            ListNode*top1=s1.top();
            ListNode*top2=s2.top();
            if(top1==top2)
            {
                s1.pop();
                s2.pop();
                ans=top1;
            }
            else
            {
                break;
            }
        }
        return ans;
    }
};
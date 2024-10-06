Given the head of a linked list, remove the nth node from the end of the list and return its head.

ListNode* removeNthFromEnd(ListNode* head, int n) 
    {
        if(head->next==NULL)    return NULL;
        ListNode*p1=NULL;
        ListNode*p2=NULL;
        ListNode*prev=NULL;
        ListNode*temp=head;
        while(temp!=NULL)
        {
            if(p2!=NULL)
            {
                prev=p2;
                p2=p2->next;
            }
            n--;
            if(n==0)
            {
                p1 = temp;
                p2 = head;
            }
            
            temp=temp->next;
        }    
        if(prev==NULL)
        {
            return head->next;
        }
        if(p2->next==NULL)
        {
            prev->next=NULL;
        }
        else
        {
            prev->next=p2->next;
        }        
        return head;
    }
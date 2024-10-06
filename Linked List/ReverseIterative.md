 ListNode* reverseList(ListNode* head) 
    {
        ListNode*temp=head;
        ListNode*prev=NULL;
        while(temp!=NULL)
        {
            ListNode*save=temp->next;
            temp->next=prev;
            prev=temp;
            temp=save;
        }
    } 
    ---------------------------------------------------------------------------
ListNode* reverseList(ListNode* head) 
    {
        if(head==NULL)  return  NULL;
        if(head->next==NULL) return head;
        ListNode*temp= reverseList(head->next);                   
        ListNode*use=temp;
        while(use->next!=NULL)
        {
            use=use->next;
        }
        use->next=head;
        head->next=NULL;
        return temp;
    }
ListNode* oddEvenList(ListNode* head) 
{
    if(head==NULL || head->next==NULL || head->next->next==NULL)
    return head;
    ListNode*odd=head;
    ListNode*even=head->next;
    ListNode*a2=even;
    while(even!=NULL && even->next!=NULL)
    {
        odd->next = even->next;
        even->next = even->next->next;
        odd=odd->next;
        even=even->next;
    }
    odd->next=a2;
    return head;
}
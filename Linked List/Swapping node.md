You are given the head of a linked list, and an integer k.

Return the head of the linked list after swapping the values of the kth node from the beginning and the kth node from the end (the list is 1-indexed).

  ListNode* swapNodes(ListNode* head, int k) 
    {        
        ListNode* p1 = NULL;
        ListNode* p2 = NULL;        
        ListNode* temp = head;        
        while(temp!=NULL) 
        {            
            if(p2 != NULL)
            p2 = p2->next;                        
            k--;
            if(k == 0) 
            {
                p1 = temp;
                p2 = head;
            }            
            temp = temp->next;
        }
        swap(p1->val, p2->val);
        return head;   
    }
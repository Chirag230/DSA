Given a linked list, the task is to reverse every k node (where k is an input to the function) in the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should be considered as a group and must be reversed (See Example 2 for clarification).

Examples:

Input: Linked List: 1->2->2->4->5->6->7->8, k = 4
Output: 4 -> 2 -> 2 -> 1 -> 8 -> 7 -> 6 -> 5 


  struct node *reverseIt(struct node *head, int k) 
    {
        // Complete this method
        if(head==NULL || head->next==NULL)
       return head;
       int count=0;
       node*curr=head;
       node*prev=NULL;
       while(curr!=NULL && count <k)
       {
           node*agla=curr->next;
           curr->next=prev;
           prev=curr;
           curr=agla;
           count++;
       }
       if(curr!=NULL)
       head->next=reverseIt(curr,k);
       
       return prev;
    }
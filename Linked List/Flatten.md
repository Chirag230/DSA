Node* mergeTwoLists(Node* head1, Node* head2) {
    // If one of the linked lists is empty, return the other
    if (head1 == NULL)
        return head2;

    if (head2 == NULL)
        return head1;

    Node* result;
    // Compare the nodes and merge them in sorted order
    if (head1->data < head2->data) {
        result = head1;
        // Recursively merge the rest of the nodes
        result->bottom = mergeTwoLists(head1->bottom, head2); //Trust
    } else {
        result = head2;
        // Recursively merge the rest of the nodes
        result->bottom = mergeTwoLists(head1, head2->bottom); //Trust
    }

    return result;
}

Node *flatten(Node *head) {
    if(!head)
        return head;

    Node* temp = flatten(head->next);
    
    return mergeTwoLists(head, temp);
}
# Delete Node in Doubly Linked List:

> Question link:
> https://www.geeksforgeeks.org/problems/delete-node-in-doubly-linked-list/1

## Approach:

### Code:

```C++
Node* deleteNode(Node *head, int x) {
    
    Node* deletedNode = NULL;

    // delete first node
    if(x == 1){
        Node* temp = head;
        Node* forward = temp-> next;
        forward -> prev = NULL;
        head = forward;
        deletedNode = temp;
    }else{

        Node* temp = head;
        while(x > 1){
            temp = temp -> next;
            x--;
        }

        if(temp -> next != NULL){
            Node* bnode = temp -> prev;
            bnode -> next = NULL;
            deletedNode = temp;
        }else{
            Node* forward = temp -> next;
            Node* bnode = temp -> prev;
            bnode -> next = forward;
            forward -> prev = bnode;
            deletedNode = temp;
        }
    }

    delete deletedNode;
    return head;
}
```

**Time Complexity:**  O(x), where `x` is the position of the node to be deleted.

**Space Complexity:** O(1), as no extra space is used.
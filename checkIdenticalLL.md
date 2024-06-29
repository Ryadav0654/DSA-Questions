# Check Given Linked list is identical or not:

> Question link:
> https://www.geeksforgeeks.org/problems/identical-linked-lists/1

### Code:
```C++
// find the length of the list
int getLength(Node* head){
    Node*  temp = head;
    int len = 0;
    while(temp != NULL){
        len++;
        temp = temp -> next;
    }
    return len;
}

// check list is identical or not 
bool areIdentical(Node *head1, Node *head2) {
    int first_len = getLength(head1);
    int second_len = getLength(head2);

    // if length is not equal return false
    if(first_len != second_len){
        return false;
    }

    while(head1 != NULL && head2 != NULL){

        if(head1 -> data != head2 -> data){
            return false;
        }
        head1 = head1 -> next;
        head2 = head2 -> next;
    }

    return true;
}

```

**Time complexity:** `O(n)`, where `n` is the length of the list.
**Space complexity:** `O(1)`, as no extra space is used.

## Optimize code:
```C++
    bool areIdentical(Node* first, Node* second){

        while(first != NULL && second != NULL ){
            if(first -> data != second -> data) return false;

            first = first -> next;
            second = second -> next;
        }

        if(first == NULL && second == NULL ) return true;
        return true;

        // or return (first == NULL && second == NULL); Here we can also use this
    }
```

- Time and space complexity is same.
# Binary Linked list to integer:

**Problem statement**

- You are given a singly linked list containing ‘n’ nodes, where every node in the linked list contains a pointer “next” which points to the next node in the list and having values either 0 or 1. Your task is to return the decimal representation of the given number in the linked list.

### Approach:

- Initialize a variable `dec` to 0 and `temp` to the head of the linked list.
- Use a while loop to traverse the linked list(temp != NULL).
- In each iteration, multiply `node data` by power of 2 and add the value of the dec to it.
- Return `dec` after exiting the loop.

### Code:

```C++
int binaryToInteger(int n, Node *head) {
    int dec = 0;
    int ex = n-1;
    Node* temp = head;
    while(temp != NULL){
        int num = temp -> data;
        // also use pow function
        dec = dec + num*(1 << ex);
        ex--;
        temp = temp -> next;
    }

    return dec;
}
```

**Time Complexity** `O(n)`, where `n` is the number of nodes in the linked list.
**Space Complexity** `O(1)`, as no extra space is used.(function)

- The space used by the linked list itself is `O(n)`, where `n` is the number of nodes in the linked list.

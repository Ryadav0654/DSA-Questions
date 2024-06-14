# Find last Node which divided by K:

> Question link:

### Approach:

1. **Calculate Length of the List**:

   - The function starts by calling the `getLength` function to find the length of the linked list. This gives the total number of nodes in the list.

2. **Find Position Divisible by k**:

   - It then initializes a variable `n` with the length of the list.
   - Using a while loop, it decrements `n` until it finds a position in the list that is divisible by `k`. This is done by checking if `n % k == 0`.
   - Once a position divisible by `k` is found, the loop breaks.

3. **Locate Node at the Found Position**:
   - After finding the position, another while loop is used to traverse the list again.
   - This time, the loop decrements `n` until it reaches 1. This step effectively finds the last node whose position is divisible by `k`.
   - During each iteration, the `temp` pointer is moved to the next node in the list.
   - Finally, the function returns the node pointer `temp`, which now points to the node whose position in the list is divisible by `k`.

### Code:

```C++
int getLength(Node* head)
{
    int len = 0;
    while(head != NULL){
        len++;
        head = head -> next;
    }

    return len;
}

Node* modularNode(int k, Node* head) {
    // find length of the list
    int n = getLength(head);
    Node* temp = head;
    // check which node position is divided by k
    while(n != 0){
        if(n%k == 0){
            break;
        }
        n--;
    }

    // find that last node which postion is divided by the k
    while( n > 1){
        temp = temp -> next;
        n--;
    }

    return temp;

}

```

**Time Complexity:** `O(n)`, where `n` is the length of the list.

**Space Complexity:** `O(1)`, as no extra space is used.

### Optimized Code:

```C++
Node* modularNode(int k, Node* head) {

    // create result node and current node
    Node* result = NULL;
    Node* current = head;

    // traverse the list
    int cnt = 0;
    while(current != NULL){
        ++cnt;
        if(cnt%k == 0){
            result = current;
        }
        current = current -> next;
    }

    return result;
}
```

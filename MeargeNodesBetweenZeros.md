#  Merge Nodes in Between Zeros:

> Question link:
> https://leetcode.com/problems/merge-nodes-in-between-zeros/description/?envType=daily-question&envId=2024-07-04


### Code:

```C++

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */

class Solution {
public:
    ListNode* mergeNodes(ListNode* head) {
        // define a new list which head is modList
        ListNode* modList = new ListNode(-1);

        // initialise the curr and temp pointer
        ListNode* curr = head;
        ListNode* temp = modList;
        int sum = 0;

        // traverse the list and summation
        while(curr != NULL){
            if(curr-> val == 0 && sum != 0){            
                ListNode* newNode  = new ListNode(sum);
                temp -> next = newNode;
                temp = newNode;
                sum = 0;
            }

            sum += curr -> val;
            curr = curr -> next;
        }

        // remove first node which value is -1
        ListNode* ans = modList -> next;
        delete modList;

        // return the ans
        return ans;
    }
};
```

**Another code:**
```C++

    ListNode* mergeNodes(ListNode* head) {
        ListNode* curr = head;
        ListNode* temp = curr;
        ListNode* forward = head -> next;
        int sum = 0;
        while(forward != NULL){
            if(forward -> val == 0 && sum != 0){            
                ListNode* newNode  = new ListNode(sum);
                temp -> next = newNode;
                temp = newNode;
                sum = 0;
            }
           else{
                 sum += forward -> val;
                 forward = forward -> next;
            }   
        }
        ListNode* ans = curr -> next;
        delete curr;
        return ans;
    }

```

## Using recursion:

### Approach:

- Store the first non-zero value, given by head->next, in head.
- If head is null, return head.
- Initialize a dummy node temp with head.
- Initialize sum with 0.
- Iterate through the list until the value of temp is not 0:
- Set temp as temp->next.
- Increment sum with the value of temp.
- Store the updated sum in the value of head.
- Store head->next as the solution of the sub-problem starting at temp, given by mergeNodes(temp).
- Return head.

### Code:

```C++
class Solution {
public:
    ListNode* mergeNodes(ListNode* head) {
        // Start with the first non-zero value.
        head = head->next;
        if (head == nullptr) {
            return head;
        }

        // Initialize a dummy head node.
        ListNode* temp = head;
        int sum = 0;
        while (temp->val != 0) {
            sum += temp->val;
            temp = temp->next;
        }

        // Store the sum in head's value.
        head->val = sum;
        // Store head's next node as the recursive result for temp node.
        head->next = mergeNodes(temp);
        return head;
    }
};
```

**Time Complexity :** `O(n)`, where `n` is the length of the list.

**Space Complexity :** `O(n)`, where `n` is the length of the list.

## Optimized Code:

### Approach:
- Initialize modify and nextSum with head->next that stores the first node with a non-zero value.
- Iterate through the list until modify is not null:
- Initialize sum with 0 to store the sum of the current block.
- Iterate through the block until nextSum encounters a 0:
    - Add the value of the current node to sum.
    - Move nextSum to the next node.
    - Modify the node value at modify to sum.
    - Move nextSum to the next node that stores the next - block's first non-zero value. Also, set modify->next to this node.
    - Move modify to it's next node.
- Return head->next

### Code:
```C++

    ListNode* mergeNodes(ListNode* head) {     
        ListNode* temp = head;
        ListNode* forward = head -> next;
        int sum = 0;
        while(forward != NULL){
            if(forward -> val == 0 && sum != 0){            
                temp -> val = sum;
                if(forward -> next == NULL){
                    temp -> next = NULL;
                    break;
                }
                temp-> next = forward;
                temp = temp-> next;
               
                sum = 0;
            }
           else{
                 sum += forward -> val;
                 forward = forward -> next;
            }   
        }

        return head;
    }

```

**Another code:**
```C++

    ListNode* mergeNodes(ListNode* head) {
        // Initialize a sentinel/dummy node with the first non-zero value.
        ListNode* modify = head->next;
        ListNode* nextSum = modify;

        while (nextSum) {
            int sum = 0;
            // Find the sum of all nodes until you encounter a 0.
            while (nextSum->val != 0) {
                sum = sum + nextSum->val;
                nextSum = nextSum->next;
            }

            // Assign the sum to the current node's value.
            modify->val = sum;
            // Move nextSum to the first non-zero value of the next block.
            nextSum = nextSum->next;
            // Move modify also to this node.
            modify->next = nextSum;
            modify = modify->next;
        }
        return head->next;
    }
```

**Time Complexity :** `O(n)`, where `n` is the length of the list.

**Space Complexity :** `O(1)`, where `n` is the length of the list.


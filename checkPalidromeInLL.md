# Linked list of strings forms a palindrome

> Question link:
> https://www.geeksforgeeks.org/problems/linked-list-of-strings-forms-a-palindrome/1

### Approach:
- initialise the empty string str
- traverse the linked list and add the node data in string str
- check string str is palidrome or not

### Code:

```C++
    // function to check string is palidrome or not 
    bool checkPalidrome(string &combineString){
        // initialise start and end
        int s = 0;
        int e = combineString.length() -1;

        // traverse the string and check
        while(s < e){
            if(combineString[s] != combineString[e]){
                return false;
            }
            s++;
            e--;
        }

        return true;
    }


    bool compute(Node* head)
    {
        string combineString = "";
        // convert linked list into string
        Node* current = head;
        while(current != NULL){
            combineString += current-> data;
            current = current -> next;
        }

        return checkPalidrome(combineString);
    }
```

**Time complexity** `O(n)` where `n` is the number of nodes in the linked list.

**Space complexity** `O(n)` to store all the node data in the string,where `n` is the number of nodes in the linked list.
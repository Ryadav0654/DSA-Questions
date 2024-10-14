# Find Height of the Binary Tree:

## Code:

```C++
int height(Node* root){

    // base case 
    if(root == NULL){
        return 0;
    }

    // find the height of left side
    int left_height = height(root-> left);

    // find the height of right side
    int right_height = height(root -> right);

    // here 1 add for root node
    int ans = max(left_height, right_height) + 1;

    return ans;
}   

```
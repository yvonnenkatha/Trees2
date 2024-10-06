class Solution {
public:
    // Helper function to compute the height of the tree and check if it is balanced
    int checkHeight(TreeNode* root) {
        if (root == nullptr) {
            return 0; // A null tree has a height of 0
        }
        
        // Check the height of the left subtree
        int leftHeight = checkHeight(root->left);
        if (leftHeight == -1) return -1; // If left subtree is not balanced
        
        // Check the height of the right subtree
        int rightHeight = checkHeight(root->right);
        if (rightHeight == -1) return -1; // If right subtree is not balanced
        
        // If the difference in heights is more than 1, the tree is not balanced
        if (abs(leftHeight - rightHeight) > 1) {
            return -1;
        }
        
        // Return the height of the tree
        return max(leftHeight, rightHeight) + 1;
    }
    
    bool isBalanced(TreeNode* root) {
        // If checkHeight returns -1, the tree is not balanced
        return checkHeight(root) != -1;
    }
};
  

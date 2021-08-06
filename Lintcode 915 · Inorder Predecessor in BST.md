# Lintcode 915 · Inorder Predecessor in BST

**# Lintcode 915 · Inorder Predecessor in BST**
**
**
public TreeNode inorderPredecessor(TreeNode root, TreeNode p) {
        // write your code here
        TreeNode currRoot = root;
        TreeNode predecessor = null;
        while (currRoot != null) {
            if (currRoot.val < p.val) {
                predecessor = currRoot;
                currRoot = currRoot.right;     
            } else {
                currRoot = currRoot.left;
            }
        }
        return predecessor;
    }
**
**
public TreeNode inorderPredecessor(TreeNode root, TreeNode p) {
        // write your code here
        if (root == null) return null;

        if (root.val < p.val) {
            TreeNode right = inorderPredecessor(root.right, p);
            return right == null ? root : right;
        } else {
            return inorderPredecessor(root.left, p);
        }
    }

### Binary Tree Maximum Path Sum
```java

/*
This problem was asked by Google.

Given a binary tree of integers, find the maximum path sum between two nodes. The path must go through at least one node, and does not need to go through the root.

LeetCode Link: https://leetcode.com/problems/binary-tree-maximum-path-sum/description/
*/

int max = Integer.MIN_VALUE;
    
public int maxPathSum(TreeNode root) {
    max = Math.max(helper(root), max);
    return max;
}
    
public int helper(TreeNode root) {
    if(root==null) return 0;
    int left = helper(root.left);
    int right = helper(root.right);
    if(left+right+root.val>max) max = left+root.val+right;
    max = Math.max(Math.max(root.val, Math.max(root.val+left, root.val+right)), max);
    return Math.max(root.val, Math.max(root.val+left, root.val+right));
}
```
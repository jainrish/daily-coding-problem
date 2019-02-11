### Binary Tree Level Order Traversal
```java

/*
This problem was asked by Microsoft.

Print the nodes in a binary tree level-wise. For example, the following should print 1, 2, 3, 4, 5.

  1
 / \
2   3
   / \
  4   5

LeetCode Link: https://leetcode.com/problems/binary-tree-level-order-traversal/description/
*/

/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

public List<Integer> levelOrder(TreeNode root) {
    List<Integer> res = new ArrayList<>();
    if(root==null) return res;

    Queue<TreeNode> q = new LinkedList<>();
    q.add(root);

    while(!q.isEmpty()) {
        int size = q.size();

        for(int i=0;i<size;i++) {
            TreeNode node = q.poll();
            if(node.left!=null)q.add(node.left);
            if(node.right!=null)q.add(node.right);
            res.add(node.val);
        }

    }
    return res;
}

```
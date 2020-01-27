# Maximum Depth of Binary Tree
## https://leetcode.com/problems/maximum-depth-of-binary-tree

Given a binary tree, find its maximum depth.

**The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.**

**Note: A leaf is a node with no children.**
```
Example:

Given binary tree [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7

return its depth = 3.
```

## Implementation : DFS

```java
public int maxDepth(TreeNode root) {
        if(root==null)
            return 0;

        int leftDepth = maxDepth(root.left);
        int rightDepth = maxDepth(root.right);

        int maxDepth = Math.max(leftDepth, rightDepth);

        return maxDepth + 1;
}
```

### Complexity analysis

Time complexity : we visit each node exactly once, thus the time complexity is O(N), where Nis the number of nodes.

Space complexity : in the worst case, the tree is completely unbalanced, e.g. each node has only left child node, the recursion call would occur N times (the height of the tree), therefore the storage to keep the call stack would be O(N). But in the best case (the tree is completely balanced), the height of the tree would be log(N). Therefore, the space complexity in this case would be O(log(N)).


# References :
https://leetcode.com/articles/maximum-depth-of-binary-tree

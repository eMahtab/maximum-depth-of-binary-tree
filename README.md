# Maximum Depth of Binary Tree ✌️
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

## Implementation 1 : DFS (Recursive)

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

**Time complexity** : we visit each node exactly once, thus the time complexity is O(N), where Nis the number of nodes.

**Space complexity** : in the worst case, the tree is completely unbalanced, e.g. each node has only left child node, the recursion call would occur N times (the height of the tree), therefore the storage to keep the call stack would be O(N). But in the best case (the tree is completely balanced), the height of the tree would be log(N). Therefore, the space complexity in this case would be O(log(N)).

# Implementation 2 : Iterative
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {
       if(root == null)
           return 0;
       
       Queue<TreeNode> q = new ArrayDeque<>();
       q.add(root);
       int maxDepth = 0; 
       while(!q.isEmpty()) {
           maxDepth++;
           int size = q.size();
           for(int i = 0; i < size; i++) {
               TreeNode current = q.poll();
               if(current.left != null)
                   q.add(current.left);
               if(current.right != null)
                   q.add(current.right);
           }
       } 
      return maxDepth;  
   }
}
```
😳 Very minute 😳
In the iterative approach make sure you only loop through the size of the array before adding child nodes of the next level. So don't do this `for(int i = 0; i < q.size(); i++)` .

# References :
https://leetcode.com/articles/maximum-depth-of-binary-tree

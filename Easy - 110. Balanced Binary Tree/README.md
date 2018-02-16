### 题意

给定一个二叉树，判断是否高度平衡。

高度平衡二叉树定义为：

> 二叉树中每个节点的子树深度差不能大于1

**Example 1:**

给定二叉树 `[3,9,20,null,null,15,7]`:

```
    3
   / \
  9  20
    /  \
   15   7
```

Return true.
**Example 2:**

给定二叉树 `[1,2,2,3,3,null,null,4,4]`:

```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4

```

Return false.

### 思路

后序遍历，若左右子树返回-1，或左右子树的深度差值大于1，返回-1。

否则返回左右子树的最大深度+1。

### 复杂度

时间复杂度：O(n)

空间复杂度：O(n)

```java
public class BalancedBinaryTree {

    /**
     time : O(n);
     space : O(n);
     * @param root
     * @return
     */
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        return helper(root) != -1;
    }

    public int helper(TreeNode root) {
        if (root == null) return 0;
        int l = helper(root.left);
        int r = helper(root.right);
        if (l == -1 || r == -1 || Math.abs(l - r) > 1) {
            return -1;
        }
        return Math.max(l, r) + 1;
    }
}
```


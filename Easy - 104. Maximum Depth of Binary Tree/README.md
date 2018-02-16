### 题意

给定一个二叉树，求出最大深度。

最大深度是最长路径上的节点数目，最长路径从根节点向下到最远叶子节点。

给定二叉树 `[3,9,20,null,null,15,7]`

```
    3
   / \
  9  20
    /  \
   15   7
```

返回值为3。

### 思路

后序遍历，若节点为空返回0，否则返回左右子节点的遍历并+1。

### 复杂度

时间复杂度：O(n)

空间复杂度：O(n)

```java
/**
 * Created by Edward on 28/07/2017.
 */

public class MaximumDepthofBinaryTree {
    /**
     * @param root
     * @return
     */
	
    public static int maxDepth(TreeNode root) {
        if (root == null) return 0;
        return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
    }

    public static int maxDepth2(TreeNode root) {
        if (root == null) return 0;
        int l = maxDepth2(root.left) + 1;
        int r = maxDepth2(root.right) + 1;
        return Math.max(l, r);
    }
}
```


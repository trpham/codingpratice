# Symmetric Tree

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

**Ideas**:

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

But the following `[1,2,2,null,3,null,3]` is not:
```
    1
   / \
  2   2
   \   \
   3    3
```
- Recursively compare the `outer lefts with the outer rights`, `inner lefts with inner rights`.

```java
public boolean isSymmetric(Node root) {

    if (root == null) return true;

    return isSymmetric(root.left, root.right);
}

public boolean isSymmetric(Node l, Node r) {

    if (l == null && r == null) return true;
    if (l == null || r == null) return false;
    if (l.val != r.val) return false;

    return isSymmetric(l.left, r.right) 
        && isSymmetric(l.right, r.left);
}
```
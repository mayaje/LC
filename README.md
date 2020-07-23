# LC

## 513. Find Bottom Left Tree Value

We can utilize a slightly modified breadth-first search (BFS) to solve this problem. BFS travels a binary tree row-by-row, and we can write it so that it travels each row from left-to-right; we can immediately see why this might be a useful approach for this problem! Typically, BFS makes use of a queue. To be more specific, what we can do for this problem is:

1. Keep track of a variable corresponding to the left-most node of a given row; create a queue that, at first, consists of the root node.
2. While the queue is not empty (in other words, while there is a new row to explore), update the variable keeping track of the left-most node to the first element of the queue (remember, we’re writing the BFS in a left-to-right manner, so the first element of the queue is the left-most entry of the current row). Then, update the queue by setting it to the children of the nodes currently in the queue, making sure to explore the left child of each node before the right child of each node. This is how we move to the next row.
3. Return the variable used to keep track of the left-most node.


We can translate the above to code (with comments) in Python:

```python
 def findBottomLeftValue(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        # initialize queue as the root
        currQueue = [root]
        # initialize the value of the current left-most node
        currLeft = 0
        while currQueue:
            # update the value of currLeft for ecah row
            currLeft = currQueue[0].val
            # add children (if they exist) to the queue from L to R
            currQueue = [child for parent in currQueue for child in (parent.left, parent.right) if child]
        return currLeft
```
### Complexity Analysis

#### Space: 
The space complexity for BFS on a binary tree is O(n), and the same is the case here. We maintain a queue that keeps track of the nodes in our tree, and it’s possible that we may need to hold all the nodes of the tree in the queue at a point in time.

#### Time: 
The time complexity for BFS on a binary tree is O(n), and the same is the case for this problem. When searching for the left-most node, it’s possible that we may have to travel through every single node in the tree (consider, for example, a tree whose nodes only have left children). 


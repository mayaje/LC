# LC



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

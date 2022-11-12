Date: 2022.11.10

#### Tree类型总结

1. 涉及到cur_sum 或者cur_path的时候, 在访问到该节点时, 就应该已经记录下来它的值. e.g.: helper(root, [root], root.val) 相关题目: 437  129
2. 分治思想在题目中经常出现
   - helper函数做的事情,返回什么值
   - 当前root节点和左右孩子节点的关系
   - 递归的base case是什么
3. serialize 和deserialize的题目总结
   - serialize 和 deserialize的题目, 一般都可以用preorder来实现. 值得注意的是, serialize的时候, 要记得维护None的节点, 给它记一个#.后面解码的时候, 就是碰到#就返回None.否则返回处理好之后的root节点. 
   - 如果是BST的话, 可以用preorder存, 因为有可以直接利用preorder结合上下界构建树的方法. (类似题目 No 1008)
4. delete一个节点之类的, 一般需要返回delete之后的树. helper的功能就是去删除当前树的不要的节点, 然后返回处理好之后的树
5. 要记得考虑root为空的情况


------
Binary Tree DFS Traversal three methods: pre-order, in-order, post-order

Principle: 

94 https://leetcode.com/problems/binary-tree-inorder-traversal/

144 https://leetcode.com/problems/binary-tree-preorder-traversal/

145 https://leetcode.com/problems/binary-tree-postorder-traversal/

------
少部分用BFS做比较方便的题：

314 https://leetcode.com/problems/binary-tree-vertical-order-traversal/description/

107 https://leetcode.com/problems/binary-tree-level-order-traversal-ii/

103 https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/

102 https://leetcode.com/problems/binary-tree-level-order-traversal/

116 https://leetcode.com/problems/populating-next-right-pointers-in-each-node/

637 https://leetcode.com/problems/average-of-levels-in-binary-tree/

总结来说就是遇到level traversal的需求 以及涉及到相对位置（“坐标”）的题

------

对比两道很相似的题目 都是vertical order traversal

314 https://leetcode.com/problems/binary-tree-vertical-order-traversal/description/

987 https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/

看似很类似，但是有个细节的要求不一样 所以做法也会不同 
对于在同一列的点的顺序问题：
314题的要求是If two nodes are in the same row and column, the order should be from **left to right**.
987题的要求是sort these nodes by their values.
假设遇到下面这种情况，这两个要求出来的结果是不同的。

**Example:**

![img](https://assets.leetcode.com/uploads/2021/01/28/vtree2-1.jpg)

```
Input: root = [3,9,8,4,0,1,7]
314 Output: [[4],[9],[3,0,1],[8],[7]]
987 Output: [[4],[9],[0,1,3],[8],[7]]
```

对于314这种要求从左到右的题，用bfs比较合适

但987就可以用dfs记录坐标然后同一列的进行排序

------

173 https://leetcode.com/problems/binary-search-tree-iterator/

BST的中序是从小到大排好序的，这题 约等于 binary tree 的in-order iterator

非递归实现二叉树的遍历 

有很多种解法：用queue的数据结构

```python
class BSTIterator:

    def __init__(self, root: Optional[TreeNode]):
        self.queue = collections.deque()
        self.inorder(root)

    def inorder(self, root):
        if not root: 
            return
        self.inorder(root.left)
        self.queue.append(root.val)
        self.inorder(root.right)

    def next(self) -> int:
        return self.queue.popleft()
        
    def hasNext(self) -> bool:
        return len(self.queue) > 0
```

用stack数据结构

优化：stack不保存被iterator访问过的点

------

Divide and Conquer

应用的数据结构：binary tree 和 array

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
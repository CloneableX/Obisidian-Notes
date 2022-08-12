### 序列

序对能够构建的重要数据结构中有一种叫做 **序列（sequence）**，它是一组有序数据对象。

#### 列表与树形结构

通过上述关于序对知识点的了解，如果使用 `cons` 嵌套构建将形成一组有序数据对象列表，它是序列数据结构的一种构建形式。除了 `cons` 嵌套的方式外，Scheme 提供了基础程式 `list` 构建列表，也就是说下列两个结构完全相等：

```scheme
(list <a1> <a2> ... <an>)

(cons <a1>
	  (cons <a2>
	         (cons ...
	                (cons <an> nil))))
```

如果对列表进行嵌套构建，将形成树形结构，例如 `(list (list 1 2) (list 3 4))` ，树形结构的运算是递归的，不过也可以将叶子节点转换为列表，便于统一使用列表的操作。

在列表表达方式统一的情况下，可以为其抽象 `map`、`filter`  和 `accumulate` 等运算程式，相当于为列表建立抽象屏障，这样做有利于避免使用列表时需要关注它的具体实现，为底层实现的修改在整个程序系统上的统一性打下良好基础。
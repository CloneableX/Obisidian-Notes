数据抽象是为了将数据对象的结构与数据对象的使用分离，与程式抽象类似。数据对象的结构依靠一组构造器和查询器表示，但单纯的构造器和查询器并不能表达数据对象的实质，它们还必须完全符合数据对象对应的特定条件。

Scheme 提供了序对相关[[Special Forms#^6d4e39|程式]] `cons`、`car` 和 `cdr` 实现抽象数据的能力。
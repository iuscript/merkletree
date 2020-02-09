# merkletree

## 文件夹目录概要

文件夹目录：

| 序号 | 文件夹/go文件           | 作用                             |
| ---- | ----------------------- | -------------------------------- |
| 1    | simple                  | 纯粹的默克尔树                   |
|      | merkle_tree.go          | MerkleTree及相关方法             |
|      | merkle_tree_test.go     | 测试文件                         |
| 2    | patricia                | 帕特里夏树树                     |
|      | patricia.go             | Trie树及常用方法                 |
|      | patricia_test.go        | 基本函数测试                     |
|      | patricia_sparse_test.go | 测试稀疏树                       |
|      | patricia_dense_test.go  | 测试紧密树                       |
|      | children.go             | 子树节点构建相关                 |
| 3    | tire                    | 改良的默克尔帕特里夏树           |
|      | trie.go                 | MPT树及常用方法                  |
|      | trie_test.go            | 测试                             |
|      | node.go                 | 节点                             |
|      | node_test.go            | 节点测试                         |
|      | hasher.go               | 哈希者，用来计算节点哈希和跟哈希 |
|      | database.go             | 数据库对象，其实是一个缓存层     |
|      | database_test.go        | 数据库测试                       |
|      | committer.go            | 提交数据到数据库                 |
|      | encoding.go             | 编码库                           |
|      | encoding_test.go        | 测试                             |
|      | errors.go               | 错误类型                         |
|      | iterator.go             | 操作者，遍历工具，迭代工具       |
|      | iterator_test.go        | 测试                             |
|      | sync.go                 | 构建树功能                       |
|      | sync_test.go            | 测试                             |
|      | sync_bloom.go           | 布隆过滤器                       |
|      | proof.go                | 默克尔证明                       |
|      | proof_test.go           | 默克尔证明测试                   |
|      | secure_trie.go          | “安全的”默克尔树                 |
|      | secure_trie_test.go     | 测试                             |
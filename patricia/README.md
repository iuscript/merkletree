## 代码走读

#### 各文件方法表

| 序号 | Go文件/函数或方法        | 作用                                        |
| ---- | ------------------------ | ------------------------------------------- |
| 1    | patricia.go              | 该文件主要实现帕特里夏树的操作方法          |
|      | MaxPrefixPerNode         | 配置trie.maxPrefixPerNode参数               |
|      | MaxChildrenPerSparseNode | 配置trie.maxChildrenPerSparseNode参数       |
|      | Clone                    | 克隆树                                      |
|      | Item                     | 返回trie.item参数，储存在root的数据项       |
|      | Insert                   | 插入数据，key,Item对，Item是一个interface   |
|      | Set                      | 更新数据                                    |
|      | Get                      | 根据key查找数据                             |
|      | Match                    | 匹配Get的返回值                             |
|      | MatchSubtree             | 匹配findSubtree的值                         |
|      | Visit                    | 通过VisitorFunc函数便利节点                 |
|      | VisitSubtree             | 同上，但值访问子树节点，子树由key值查询获得 |
|      | VisitPrefixes            | 同上                                        |
|      | Delete                   | 删除节点                                    |
|      | DeleteSubtree            | 删除子树                                    |
| 2    | children.go              |                                             |
|      | Len                      | 树的切片长度                                |
|      | Less                     | 比较切片中树的大小                          |
|      | Swap                     | 交换切片中树的顺序                          |
|      | newSparseChildList       | 新建稀疏树的节点                            |
|      | sparseChildList.length   | 稀疏树的长度                                |
|      | sparseChildList.head     | 返回第一个child                             |
|      | sparseChildList.add      | 添加一个child                               |
|      | sparseChildList.remove   | 删除一个child                               |
|      | sparseChildList.replace  | 替换child                                   |
|      | sparseChildList.next     | 查找child                                   |
|      | sparseChildList.walk     | 查找child并执行处理函数                     |
|      | sparseChildList.total    | 子节点数量                                  |
|      | sparseChildList.clone    | 克隆                                        |
|      | sparseChildList.print    | 输出child                                   |
|      | newDenseChildList        | 新建紧密树的节点                            |


#### 单元测试

| 序号 | Go文件/测试用例方法              | 说明                                 |
| ---- | -------------------------------- | ------------------------------------ |
| 1    | patricia_test.go                 | 测试用例                             |
|      | TestTrie_ConstructorOptions      | 通过构造options创建树                |
|      | TestTrie_GetNonexistentPrefix    | 查找一个不在树中的前缀               |
|      | TestTrie_RandomKitchenSink       | 随机测试插入、删除功能               |
|      | TestTrie_DeleteRoot              | 测试添加、删除                       |
|      | TestTrie_DeleteAbsentPrefix      | 删除一个不存在的前缀                 |
| 2    | patricia_sparse_test.go          | 稀疏树测试                           |
|      | TestTrie_InsertDifferentPrefixes | 插入完全不同的前缀                   |
|      | TestTrie_InsertDuplicatePrefixes | 插入重复的前缀                       |
|      | TestTrie_InsertVariousPrefixes   | 插入各种前缀（有不同的，也有重复的） |
|      | TestTrie_InsertAndMatchPrefix    | 测试寻找一个前缀是否在树中有包含     |
|      | TestTrie_SetGet                  | 测试更新、查询功能                   |
|      | TestTrie_Match                   | 返回前缀是否在树中                   |
|      | TestTrie_MatchFalsePositive      | 功能同上                             |
|      | TestTrie_MatchSubtree            | 功能同上                             |
|      | TestTrie_Visit                   | 测试Visit函数                        |
|      | TestTrie_VisitSkipSubtree        | 同上                                 |
|      | TestTrie_VisitReturnError        | 同上                                 |
|      | TestTrie_VisitSubtree            | 同上                                 |
|      | TestTrie_VisitPrefixes           | 同上                                 |
|      | TestPatriciaTrie_CloneSparse     | 测试克隆                             |
|      | TestParticiaTrie_Delete          | 删除                                 |
|      | TestTrie_compact                 | 测试紧凑模式                         |
| 3    | patricia_dense_test.go           | 紧密树测试                           |
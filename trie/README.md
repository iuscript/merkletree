## 代码走读

### 各文件方法表

| 序号 | Go文件/函数或方法 | 作用                                                         |
| :--: | ----------------- | ------------------------------------------------------------ |
|  1   | tire.go           | tire结构的定义及大部分方法，用于生成MPT                      |
|      | SetCacheLimit     | 设置要保留的缓存生成数                                       |
|      | newFlag           | 新建一个nodeFlag对象                                         |
|      | NodeIterator      | 结点迭代器（操作员）                                         |
|      | Get               | 根据key返回value                                             |
|      | TryGet            | 将key编码成16进制，调用tryGet函数查询结点值                  |
|      | tryGet            | 查询结点value                                                |
|      | Update            | 更新结点                                                     |
|      | TryUpdate         | 更新结点value，如果结点值为零则删除结点                      |
|      | insert            | 插入结点                                                     |
|      | Delete            | 删除结点                                                     |
|      | TryDelete         | 删除结点                                                     |
|      | delete            | 删除结点                                                     |
|      | concat            | 连接2个byte切片                                              |
|      | resolve           | 还原hashNode，从数据库中提取数据                             |
|      | resolveHash       | 从数据库中提取数据，并还原hashNode                           |
|      | Root              | 返回默克尔树的哈希根                                         |
|      | Hash              | 返回默克尔树的哈希根                                         |
|      | Commit            | 返回默克尔树的哈希根，同时                                   |
|      | hashRoot          | 通过Hasher.hash方法计算哈希值                                |
|      | New               | 返回一个trie对象                                             |
|  2   | proof.go          | 包含tire结构和SecureTrie结构的默克尔证明和校验方法           |
|      | Prove             | 证明构造密钥的merkle证明                                     |
|      | VerifyProof       | 校验merkle证明                                               |
|  3   | hasher.go         | 定义了hasher结构及方法，用于                                 |
|      | newHasher         | 返回一个hasher对象                                           |
|      | hash              | 实现了从某个结点开始计算子树的哈希的功能                     |
|      | hashChildren      | 替换子节点为hashNode，同时用cache将源节点缓存                |
|      | store             | 结点存入数据库并返回一个hashNode结点                         |
|      | makeHashNode      | 生成一个hashNode                                             |
|  4   | node.go           | 定义了一个Trie树中所有结点的类型和解析的代码                 |
|      | EncodeRLP         | 将fullNode编码为一致的RLP格式                                |
|      | copy              | 复制结点                                                     |
|      | cache             | 返回flags中的hash参数。该参数是之前生成的一个hashNode结点    |
|      | String            | 打印结点                                                     |
|      | mustDecodeNode    | 解码结点                                                     |
|  5   | iterator.go       | 定义了所有枚举相关接口和实现                                 |
|      | NewIterator       | 返回一个迭代器                                               |
|      | Next              | 下一个                                                       |
|      | Prove             | 上一个                                                       |
|      | Hash              | 返回hash                                                     |
|      | Parent            | 起源                                                         |
|      | Leaf              | 返回十六进制键是否具有终止符标志                             |
|      | LeafKey           | 返回证明的路径                                               |
|  6   | sync.go           | 实现了SyncTrie对象的定义和所有方法                           |
|      | NewSync           | 生成一个新的TrieSync对象并调用AddSubTrie方法为同步root结点作准备 |
|      | AddSubTrie        | 向同步代码注册一个新的trie，根位于指定的父级                 |
|      | Missing           | 返回待同步结点的哈希                                         |
|      | Process           | 当调用者通过网络获取到这些结点的数据时，它会调用Process进行处理 |
|      | Commit            | 将存储在内部membatch中的数据刷新到持久存储中                 |
|      | Pending           | 获取当前的Trie对象有几个结点待同步                           |
|      | schedule          | 将新的状态检索请求插入到提取队列中                           |
|      | children          | 检索丢失的子项                                               |
|  7   | encoding.go       | 编解码                                                       |
|  8   | database.go       | 实现了`Database`对象的主要逻辑功能                           |
|      | NewDatabase       | 返回Database对象                                             |
|      | DiskDB            | 返回数据库                                                   |
|      | InsertBlob        | 将新的引用跟踪blob写入内存数据库                             |
|      | Node              | 节点从内存中检索编码的缓存trie节点                           |
|      | Nodes             | 检索内存数据库中缓存的所有节点的哈希值                       |
|      | Reference         | 将新引用从父节点添加到子节点                                 |
|      | Dereference       | 从根节点移除现有引用                                         |
|      | Cap               | 迭代刷新旧的但仍然引用的trie节点                             |
|      | Commit            | 遍历特定节点的所有子节点，写入数据库                         |
|      | Size              | 返回持久数据库层前面的内存缓存的当前存储大小                 |
|  9   | secure_trie.go    | 实现了SecureTrie对象，其中方法都是调用的trie对象的方法       |
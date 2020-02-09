## 代码走读

#### 各文件方法表

| 序号 | Go文件/函数或方法 | 作用                         |
| ---- | ----------------- | ---------------------------- |
| 1    | merkle_tree.go    | 该文件主要实现默克尔树操作方法 |
|      | node              | 节点struct                   |
|      | String            | 节点输出成字符串             |
|      | verifyNode        | 校验节点                     |
|      | calculateNodeHash | 计算节点哈希                 |
|      | NewTree           | 用符合接口的内容新建一棵树   |
|      | GetMerklePath     | 获取默克尔路径               |
|      | MerkleRoot        | 返回哈希根                   |
|      | RebuildTree       | 重构树                       |
|      | RebuildTreeWith   | 使用另外的内容重构树         |
|      | VerifyTree        | 校验树                       |
|      | VerifyContent     | 验证内容                     |
|      | String            | 树输出字符串                 |

#### 单元测试

| 序号 | Go文件/测试用例方法            | 说明                               |
| ---- | ------------------------------ | ---------------------------------- |
| 1    | merkle_tree_test.go            | 测试用例                           |
|      | TestNewTree                    | 测试新建树                         |
|      | TestNewTreeWithHashingStrategy | 测试新建树，并附加执行（加密）策略 |
|      | TestMerkleTree_MerkleRoot      | 测试生成哈希根                     |
|      | TestMerkleTree_RebuildTree     | 测试重构树                         |
|      | TestMerkleTree_RebuildTreeWith | 测试用新内容重构树                 |
|      | TestMerkleTree_VerifyTree      | 测试校验树                         |
|      | TestMerkleTree_VerifyContent   | 测试校验内容                       |
|      | TestMerkleTree_String          | 测试生成字符串                     |
|      | TestMerkleTree_MerklePath      | 测试梅克尔证明路径                 |
# 索引与暂存区

> 源文件：`dulwich/index.py`

##  学习目标

理解 Git 索引（暂存区）的实现，以及它在 Git 三段式工作流中的作用。

##  三段式工作流

```
工作区 (Working Directory)
    ↓ git add
暂存区 (Staging Area / Index)
    ↓ git commit
仓库 (Repository / .git)
```

##  索引文件格式

### 文件位置
`.git/index`

### 二进制格式
```
Header:
  - Signature: "DIRC" (4 bytes)
  - Version: 2, 3, or 4 (4 bytes)
  - Entry count (4 bytes)

Entry:
  - ctime, mtime (文件时间戳)
  - dev, ino (设备号、inode)
  - mode (文件模式)
  - uid, gid (用户/组 ID)
  - file size (文件大小)
  - SHA-1 (对象哈希)
  - flags (标志位)
  - path (文件路径)

Extensions:
  - Tree cache
  - Resolve undo
  - ...
```

##  核心类

### Index
索引文件的抽象。

### IndexEntry
单个文件的索引条目。

### 核心方法
- `read(path)` - 读取索引文件
- `write(path)` - 写入索引文件
- `commit(object_store)` - 从索引创建 Tree 对象
- `changes_from_tree()` - 与 Tree 对比变化

##  关键概念

### 索引条目包含什么？
- 文件路径
- 文件内容的 SHA-1（Blob 对象）
- 文件元数据（时间戳、权限等）
- Stage 标记（用于合并冲突）

### Stage 编号
- 0: 正常状态
- 1: 共同祖先
- 2: 当前分支
- 3: 要合并的分支

##  代码示例

### 读取索引
```python
# TODO: 补充代码示例
```

### 添加文件到索引
```python
# TODO: 补充代码示例
```

### 从索引创建 Tree
```python
# TODO: 补充代码示例
```

### 对比索引和工作区
```python
# TODO: 补充代码示例
```

##  关键实现细节

### 索引排序
索引条目按路径排序，为什么？

### 树缓存（Tree Cache）
优化 `git commit` 性能的机制。

### 稀疏检出
如何支持部分检出？

##  思考题

1. 为什么需要索引这个中间层？直接从工作区提交不行吗？
2. 索引文件如何处理大量文件的性能问题？
3. `git add -p` 如何实现部分暂存？
4. 索引损坏如何恢复？

---

**下一步**：学习具体命令实现，从 [git init](commands/init.md) 开始。

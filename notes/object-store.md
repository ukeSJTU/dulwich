# 对象存储

> 源文件：`dulwich/object_store.py`

##  学习目标

理解 Git 对象如何存储在 `.git/objects/` 目录中，以及 Pack 文件的作用。

##  Loose Objects（松散对象）

### 存储路径
```
.git/objects/ab/cdef1234567890... (SHA-1 的前 2 位 / 后 38 位)
```

### 存储格式
- **压缩方式**：zlib
- **文件内容**：`<type> <size>\0<content>` 压缩后的结果

### 读取流程
TODO: 补充

### 写入流程
TODO: 补充

##  Pack Files（打包文件）

### 为什么需要 Pack？
- 节省磁盘空间
- 提高网络传输效率
- 相似内容使用 delta 压缩

### Pack 文件格式
```
.git/objects/pack/pack-<SHA-1>.pack
.git/objects/pack/pack-<SHA-1>.idx
```

### Delta 压缩
TODO: 补充

##  ObjectStore 类

### 核心方法
- `__contains__()` - 检查对象是否存在
- `__getitem__()` - 获取对象
- `add_object()` - 添加对象
- `add_objects()` - 批量添加对象

### 实现类
- `DiskObjectStore` - 基于磁盘的存储
- `MemoryObjectStore` - 基于内存的存储
- `PackBasedObjectStore` - 基于 Pack 的存储

##  关键实现细节

### 对象查找顺序
1. Loose objects
2. Pack files
3. Alternates (如果配置)

### 对象写入策略
TODO: 补充

### Pack 文件索引
TODO: 补充

##  代码示例

### 读取对象
```python
# TODO: 补充代码示例
```

### 写入对象
```python
# TODO: 补充代码示例
```

### 遍历所有对象
```python
# TODO: 补充代码示例
```

##  思考题

1. 为什么 SHA-1 的前 2 位用作目录名？
2. Pack 文件如何提高 `git clone` 的速度？
3. 什么时候会触发 `git gc`（垃圾回收）？
4. Alternates 机制有什么用途？

---

**下一步**：学习 [仓库抽象](repo.md)，了解如何通过 `Repo` 类访问对象存储。

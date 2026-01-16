# 引用系统

> 源文件：`dulwich/refs.py`

##  学习目标

理解 Git 的引用机制，包括分支、标签和 HEAD 的实现原理。

##  引用类型

### 1. HEAD
- **作用**：指向当前分支
- **格式**：
  - 符号引用：`ref: refs/heads/main`
  - 分离头指针：直接存 SHA-1
- **文件位置**：`.git/HEAD`

### 2. 分支 (refs/heads/*)
- **作用**：指向某个提交
- **文件位置**：`.git/refs/heads/<branch-name>`
- **内容**：40 字符的 SHA-1

### 3. 标签 (refs/tags/*)
- **轻量标签**：直接指向 commit SHA
- **附注标签**：指向 tag 对象 SHA
- **文件位置**：`.git/refs/tags/<tag-name>`

### 4. 远程跟踪分支 (refs/remotes/*)
- **作用**：记录远程分支的位置
- **文件位置**：`.git/refs/remotes/<remote>/<branch>`

##  核心类

### RefsContainer（抽象基类）
定义引用容器接口。

### DiskRefsContainer
基于文件系统的引用存储。

### PackedRefsContainer  
打包引用（优化性能）。

##  关键操作

### 读取引用
```python
# TODO: 补充代码示例
```

### 写入引用
```python
# TODO: 补充代码示例
```

### 解析符号引用
```python
# TODO: 补充代码示例
```

### 删除引用
```python
# TODO: 补充代码示例
```

##  Packed Refs

### 为什么需要打包？
- 减少小文件数量
- 提高读取性能

### 文件格式
```
.git/packed-refs
```

### 优先级
Loose refs > Packed refs

##  关键实现细节

### refspec 解析
TODO: 补充

### 符号引用链
如何处理 `HEAD → refs/heads/main → commit SHA`？

### 引用命名规则
- 不能以 `-` 开头
- 不能包含 `..`
- 不能以 `.lock` 结尾

##  代码示例

### 创建分支
```python
# TODO: 补充代码示例
```

### 删除分支
```python
# TODO: 补充代码示例
```

### 移动分支指针
```python
# TODO: 补充代码示例
```

##  思考题

1. 为什么 HEAD 使用符号引用而不是直接存 SHA-1？
2. 分离头指针状态是什么？有什么用？
3. 为什么远程分支用 `refs/remotes/` 而不是 `refs/heads/`？
4. 如何实现原子性的引用更新？

---

**下一步**：学习 [索引与暂存区](index.md)，了解 `git add` 的工作原理。

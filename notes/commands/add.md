# git add - 添加文件到暂存区

> 源文件：`dulwich/porcelain.py` 中的 `add()` 函数  
> CLI 入口：`dulwich/cli.py` 中的 `cmd_add`

##  功能说明

将工作区的文件变更添加到暂存区（索引）。

##  命令格式

```bash
dulwich add <pathspec>...
dulwich add .  # 添加所有变更
```

##  实现流程

### 1. CLI 层（cli.py）
```python
class cmd_add(Command):
    def run(self, argv: Sequence[str]) -> None:
        # 解析路径参数
        # 特殊处理 "."
        # 调用 porcelain.add()
```

### 2. Porcelain 层（porcelain.py）
```python
def add(repo=".", paths=None):
    # TODO: 补充实现步骤
```

### 3. 核心步骤
1. TODO: 读取文件内容
2. TODO: 计算 SHA-1
3. TODO: 创建 Blob 对象
4. TODO: 存储到 object_store
5. TODO: 更新 index

##  代码分析

### 关键代码片段
```python
# TODO: 摘录关键代码并注释
```

### Blob 对象创建
```python
# TODO: 如何从文件内容创建 Blob
```

### 索引更新
```python
# TODO: 如何更新 .git/index
```

##  深入细节

### SHA-1 计算
```python
# 格式：blob <size>\0<content>
# TODO: 补充计算示例
```

### 文件模式
- `100644` - 普通文件
- `100755` - 可执行文件
- `120000` - 符号链接

### Git 对象去重
如果文件内容相同，会复用同一个 Blob 对象。

##  实验验证

### 实验 1：添加新文件
```bash
# TODO: 补充实验步骤
# 1. 创建文件
# 2. git add
# 3. 查看 .git/objects/
# 4. 查看 .git/index
```

### 实验 2：添加修改的文件
```bash
# TODO: 补充实验步骤
```

### 实验 3：添加相同内容的文件
```bash
# TODO: 验证对象去重
```

##  与 git commit 的关系

```
工作区文件 → git add → Blob 对象 + Index 条目
                      ↓
                  git commit → Tree 对象 + Commit 对象
```

##  思考题

1. `git add .` 和 `git add -A` 有什么区别？
2. 为什么大文件 `git add` 会很慢？
3. `.gitignore` 是如何生效的？
4. `git add -p` 如何实现交互式暂存？

---

**下一步**：学习 [git commit](commit.md)，了解如何从暂存区创建提交。

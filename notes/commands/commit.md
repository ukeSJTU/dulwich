# git commit - 创建提交

> 源文件：`dulwich/porcelain.py` 中的 `commit()` 函数  
> CLI 入口：`dulwich/cli.py` 中的 `cmd_commit`

##  功能说明

将暂存区的内容创建为一个新的提交对象。

##  命令格式

```bash
dulwich commit [-m <message>] [--author <author>]
```

### 参数
- `-m, --message` - 提交信息
- `--author` - 作者信息（格式：Name <email>）
- `--amend` - 修改上一次提交

##  实现流程

### 1. CLI 层（cli.py）
```python
class cmd_commit(Command):
    def run(self, args: Sequence[str]) -> int | None:
        # 解析参数
        # 如果没有 -m，启动编辑器
        # 调用 porcelain.commit()
```

### 2. Porcelain 层（porcelain.py）
```python
def commit(
    repo=".",
    message=None,
    author=None,
    committer=None,
    ...
):
    # TODO: 补充实现步骤
```

### 3. 核心步骤
1. TODO: 从 index 创建 Tree 对象
2. TODO: 获取 parent commit（HEAD）
3. TODO: 创建 Commit 对象
4. TODO: 写入对象库
5. TODO: 更新 HEAD 引用

##  代码分析

### Tree 对象构建
```python
# TODO: 如何从 index 构建 Tree
# Index 是扁平结构，Tree 是嵌套结构
```

### Commit 对象格式
```
tree <tree-sha>
parent <parent-sha>
author Name <email> <timestamp> <timezone>
committer Name <email> <timestamp> <timezone>

<commit message>
```

### HEAD 更新
```python
# TODO: 如何原子性更新 refs/heads/<branch>
```

##  深入细节

### 首次提交（没有 parent）
如何处理仓库的第一个提交？

### 合并提交（多个 parent）
`git merge` 后的提交如何表示？

### Author vs Committer
- Author: 代码作者
- Committer: 提交者（可能是不同的人）

### 时间戳格式
```
1234567890 +0800
```

##  实验验证

### 实验 1：创建首次提交
```bash
# TODO: 补充实验步骤
# 1. git init
# 2. echo "hello" > file.txt
# 3. git add file.txt
# 4. git commit -m "Initial commit"
# 5. 查看 .git/objects/
# 6. 查看 HEAD 和 refs/heads/main
```

### 实验 2：查看 Commit 对象
```bash
# TODO: 如何查看 commit 对象内容
```

### 实验 3：多层 Tree
```bash
# TODO: 创建目录结构，观察 Tree 对象嵌套
```

##  对象图示例

```
Commit (abc123)
  ├─ tree: def456
  └─ parent: 789abc

Tree (def456)
  ├─ 100644 blob 111222 file.txt
  └─ 040000 tree 333444 src/

Tree (333444)
  └─ 100644 blob 555666 main.py
```

##  思考题

1. 为什么需要 Tree 对象而不是直接在 Commit 中列出所有文件？
2. 空目录能被提交吗？为什么？
3. 如果 `git commit` 被中断，会留下什么？
4. `.git/COMMIT_EDITMSG` 文件的作用是什么？

---

**下一步**：学习 [git log](log.md)，了解如何遍历提交历史。

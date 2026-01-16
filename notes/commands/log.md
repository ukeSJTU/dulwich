# git log - 查看提交历史

> 源文件：`dulwich/porcelain.py` 中的 `log()` 函数  
> CLI 入口：`dulwich/cli.py` 中的 `cmd_log`

##  功能说明

显示提交历史记录。

##  命令格式

```bash
dulwich log [--reverse] [--name-status] [<paths>...]
```

### 参数
- `--reverse` - 反向显示（从旧到新）
- `--name-status` - 显示每次提交修改的文件
- `<paths>` - 只显示影响指定路径的提交

##  实现流程

### 1. CLI 层（cli.py）
```python
class cmd_log(Command):
    def run(self, args: Sequence[str]) -> None:
        # 解析参数
        # 使用 pager 输出
        # 调用 porcelain.log()
```

### 2. Porcelain 层（porcelain.py）
```python
def log(
    repo=".",
    paths=None,
    reverse=False,
    name_status=False,
    ...
):
    # TODO: 补充实现步骤
```

### 3. 核心步骤
1. TODO: 获取 HEAD commit
2. TODO: 遍历 parent 链
3. TODO: 格式化输出每个 commit
4. TODO: 可选：过滤路径相关的 commit

##  代码分析

### Commit 遍历算法
```python
# TODO: 如何遍历提交历史
# 深度优先 vs 广度优先
```

### 输出格式
```
commit <sha>
Author: <author>
Date:   <date>

    <message>
```

### 路径过滤
如何只显示影响特定文件的提交？

##  深入细节

### 合并提交的遍历
遇到多个 parent 如何处理？

### 性能优化
- 限制遍历深度
- 缓存机制
- 提前终止

### --name-status 实现
需要对比相邻 commit 的 tree。

##  实验验证

### 实验 1：基本使用
```bash
# TODO: 补充实验步骤
```

### 实验 2：查看特定文件历史
```bash
# TODO: git log -- <file>
```

### 实验 3：对比不同格式
```bash
# TODO: --oneline, --graph 等
```

##  与 git show 的关系

- `git log`: 显示多个提交
- `git show`: 显示单个提交详情（包括 diff）

##  思考题

1. 如何实现 `git log --graph`（ASCII 图形）？
2. 如何高效地查找包含某个字符串的提交？
3. `git log --all` 和 `git log HEAD` 有什么区别？
4. 如何实现 `git log --since="2 weeks ago"`？

---

**下一步**：学习 [git status](status.md)，了解如何显示工作区状态。

# git status - 查看工作区状态

> 源文件：`dulwich/porcelain.py` 中的 `status()` 函数  
> CLI 入口：`dulwich/cli.py` 中的 `cmd_status`

##  功能说明

显示工作区和暂存区的状态，包括已修改、已暂存、未跟踪的文件。

##  命令格式

```bash
dulwich status [<paths>...]
```

##  实现流程

### 1. CLI 层（cli.py）
```python
class cmd_status(Command):
    def run(self, args: Sequence[str]) -> None:
        # 解析参数
        # 调用 porcelain.status()
        # 格式化输出
```

### 2. Porcelain 层（porcelain.py）
```python
def status(repo="."):
    # TODO: 补充实现步骤
    # 返回 staged, unstaged, untracked 三个列表
```

### 3. 核心步骤
1. TODO: 读取 index（暂存区）
2. TODO: 读取 HEAD tree（上次提交）
3. TODO: 扫描工作区文件
4. TODO: 三方对比

##  代码分析

### 三方对比
```
HEAD Tree ← 对比 → Index ← 对比 → Working Directory
   (已提交)        (已暂存)         (工作区)
```

### 文件状态分类
```python
# Staged (Changes to be committed)
- new file (在 index 中，不在 HEAD 中)
- modified (在 index 和 HEAD 中，内容不同)
- deleted (在 HEAD 中，不在 index 中)

# Unstaged (Changes not staged)
- modified (在 index 和工作区中，内容不同)
- deleted (在 index 中，工作区不存在)

# Untracked
- 在工作区，不在 index 中
```

##  深入细节

### 如何高效对比？
- 使用文件 mtime 快速判断
- 只对可能变更的文件计算 SHA-1

### .gitignore 的处理
如何判断文件是否应该显示为 untracked？

### 子模块状态
如何显示子模块的状态？

##  实验验证

### 实验 1：各种状态
```bash
# TODO: 补充实验步骤
# 1. 创建新文件（untracked）
# 2. git add（staged）
# 3. 修改文件（unstaged）
# 4. git status 查看
```

### 实验 2：理解输出格式
```bash
# TODO: 分析 status 输出的每一部分
```

### 实验 3：性能测试
```bash
# TODO: 大仓库中 status 的性能
```

##  状态输出示例

```
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   new.txt
        modified:   modified.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes)
        modified:   modified.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        untracked.txt
```

##  思考题

1. 为什么同一个文件可以同时出现在 staged 和 unstaged？
2. `git status -s` 的短格式如何实现？
3. 如何优化大仓库的 `git status` 性能？
4. `.git/index` 损坏后 `git status` 会怎样？

---

##  阶段总结

恭喜！你已经学习完成了 Git 核心工作流：

```
init → add → commit → log → status
```

**建议实践**：
1. 用 Dulwich 实现一个简化版的 Git
2. 用学到的知识调试真实的 Git 问题
3. 阅读更多高级命令实现（merge, rebase, etc.）

---

**进阶主题**（可选）：
- [git diff](diff.md) - 对比差异
- [git branch](branch.md) - 分支管理
- [git merge](merge.md) - 合并分支
- [git clone](clone.md) - 克隆仓库
- [git fetch/push](fetch-push.md) - 远程操作

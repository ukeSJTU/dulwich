按照约定：

```bash
$ uv venv
$ source ./.venv/bin/activate
$ pip install -e ".[dev]"
```

运行：

```bash
$ dulwich --help
usage: dulwich [-h] [--no-pager] [--pager] [command]

Simple command-line interface to Dulwich

positional arguments:
  command     Command to run. Available: add, annotate, archive, bisect, blame, branch, bundle, check-ignore, check-mailmap,
              checkout, cherry, cherry-pick, clone, column, commit, commit-tree, config, count-objects, daemon, describe, diagnose,
              diff, diff-tree, dump-index, dump-pack, fetch, fetch-pack, filter-branch, for-each-ref, format-patch, fsck, gc, grep,
              help, init, interpret-trailers, lfs, log, ls-files, ls-remote, ls-tree, mailinfo, mailsplit, maintenance, merge,
              merge-base, merge-tree, mv, notes, pack-objects, pack-refs, prune, pull, push, rebase, receive-pack, reflog, remote,
              repack, replace, rerere, reset, restore, rev-list, revert, rm, shortlog, show, show-branch, show-ref, stash, status,
              stripspace, submodule, switch, symbolic-ref, tag, unpack-objects, update-server-info, upload-pack, var, verify-commit,
              verify-tag, web-daemon, worktree, write-tree

options:
  -h, --help  show this help message and exit
  --no-pager  Disable pager
  --pager     Force enable pager
```

因为 `pyproject.toml` 里配置了:

```toml
[project.scripts]
dulwich = "dulwich.cli:main"
```

其他配置文件可以看 [`notes/configs.md`](configs.md)，这里不展开。

因此我们从 [`dulwich/cli.py`](../dulwich/cli.py) 的 `main` 函数开始看起。

> VSCode 小技巧，可以用 Command+Shift+O 输入 `main`，快速跳转到已经打开的 editor 中 `main` 函数定义处。当然也可以 Command+P 输入 `cli@main` 来跳转。

Python 语法相关的笔记都放在 [`notes/syntax.md`](syntax.md)。

##  学习路径

### 阶段 0：CLI 层（已完成 ）
1. **[CLI 架构分析](cli-architecture.md)** - 命令行工具的整体设计
    - 两阶段参数解析
    - 命令模式 + 注册表模式
    - argparse 高级用法
    - 输出流管理（AutoFlush、Pager）

### 阶段 1：Git 对象模型（核心基础）
2. **[Git 对象模型](objects.md)** - Git 的核心数据结构
    - `ShaFile` 基类
    - `Blob` - 文件内容
    - `Tree` - 目录结构
    - `Commit` - 提交记录
    - `Tag` - 标签对象

3. **[对象存储](object-store.md)** - 对象的存储与读取
    - `.git/objects/` 目录结构
    - 对象的序列化与反序列化
    - Pack 文件（压缩存储）

### 阶段 2：仓库抽象（容器）
4. **[仓库抽象](repo.md)** - Git 仓库的统一接口
    - `Repo` 类的作用
    - `.git/` 目录结构
    - 如何访问对象、引用、索引

### 阶段 3：引用系统（指针）
5. **[引用系统](refs.md)** - Git 的指针机制
    - `HEAD` - 当前分支指针
    - `refs/heads/*` - 分支
    - `refs/tags/*` - 标签
    - `refs/remotes/*` - 远程跟踪分支

### 阶段 4：索引/暂存区（临时存储）
6. **[索引与暂存区](index.md)** - git add 的秘密
    - `.git/index` 文件格式
    - `IndexEntry` 结构
    - 工作区 → 暂存区 → 仓库

### 阶段 5：Porcelain API（高层命令）
7. **[git init](commands/init.md)** - 初始化仓库
8. **[git add](commands/add.md)** - 添加文件到暂存区
9. **[git commit](commands/commit.md)** - 创建提交
10. **[git log](commands/log.md)** - 查看提交历史
11. **[git status](commands/status.md)** - 查看工作区状态

---

##  推荐学习顺序

**混合路径**（理论 + 实践）：
```
objects.md → init.md → add.md → 
object-store.md → index.md → 
commit.md → refs.md → log.md → status.md
```

**学习方法**：
1. 阅读源码前先看笔记框架
2. 在源码中验证笔记内容
3. 补充自己的理解和发现
4. 用注释或示例代码加深记忆



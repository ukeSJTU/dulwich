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

## 学习笔记

1. **[CLI 架构分析](cli-architecture.md)** - 命令行工具的整体设计
    - 两阶段参数解析
    - 命令模式 + 注册表模式
    - argparse 高级用法
    - 输出流管理（AutoFlush、Pager）



# git init - 初始化仓库

> 源文件：`dulwich/porcelain.py` 中的 `init()` 函数  
> CLI 入口：`dulwich/cli.py` 中的 `cmd_init`

##  功能说明

创建一个新的 Git 仓库或重新初始化现有仓库。

##  命令格式

```bash
dulwich init [--bare] [--objectformat=<format>] [<path>]
```

### 参数
- `--bare` - 创建裸仓库（没有工作目录）
- `--objectformat` - 对象哈希算法（sha1 或 sha256）
- `<path>` - 仓库路径（默认当前目录）

##  实现流程

### 1. CLI 层（cli.py）
```python
class cmd_init(Command):
    def run(self, args: Sequence[str]) -> None:
        # 解析参数
        # 调用 porcelain.init()
```

### 2. Porcelain 层（porcelain.py）
```python
def init(path=".", bare=False, object_format=None):
    # TODO: 补充实现步骤
```

### 3. 需要创建的目录和文件
```
.git/
├── objects/
│   ├── info/
│   └── pack/
├── refs/
│   ├── heads/
│   └── tags/
├── HEAD             # ref: refs/heads/main
├── config           # 仓库配置
└── description      # 仓库描述
```

##  代码分析

### 关键代码片段
```python
# TODO: 摘录关键代码并注释
```

### 核心逻辑
1. TODO: 检查路径是否存在
2. TODO: 创建 .git 目录结构
3. TODO: 初始化 HEAD
4. TODO: 写入默认配置

##  深入细节

### 裸仓库 vs 普通仓库
TODO: 区别和使用场景

### 对象格式选择
- SHA-1: 传统格式
- SHA-256: 新格式（抗碰撞）

### 默认分支名
如何确定初始分支名（main vs master）？

##  实验验证

### 实验 1：创建普通仓库
```bash
# TODO: 补充实验步骤
```

### 实验 2：创建裸仓库
```bash
# TODO: 补充实验步骤
```

### 实验 3：查看初始化结果
```bash
# TODO: 补充验证命令
```

##  思考题

1. 为什么 `.git/` 是隐藏目录？
2. 在已有仓库上再次执行 `git init` 会发生什么？
3. 裸仓库为什么不需要工作目录？
4. 如何在 `git init` 时指定默认分支名？

---

**下一步**：学习 [git add](add.md)，了解如何将文件添加到暂存区。

# 仓库抽象

> 源文件：`dulwich/repo.py`

##  学习目标

理解 `Repo` 类如何作为 Git 仓库的统一入口，管理对象、引用和索引。

##  Repo 类

### 作用
提供对 Git 仓库各个组件的统一访问接口。

### 核心属性
- `object_store` - 对象存储
- `refs` - 引用管理
- `index` - 索引（暂存区）
- `path` - 仓库路径
- `bare` - 是否为裸仓库

### 核心方法
- `__init__(path)` - 打开仓库
- `get_config()` - 获取配置
- `get_config_stack()` - 获取配置栈
- `head()` - 获取 HEAD 指向的 SHA
- `do_commit()` - 底层提交方法

##  .git/ 目录结构

```
.git/
├── objects/          # 对象存储
│   ├── info/
│   └── pack/
├── refs/             # 引用
│   ├── heads/        # 分支
│   ├── tags/         # 标签
│   └── remotes/      # 远程跟踪分支
├── HEAD              # 当前分支指针
├── index             # 暂存区
├── config            # 仓库配置
├── description       # 仓库描述
└── hooks/            # Git 钩子
```

##  仓库类型

### 普通仓库 (Non-bare)
- 有工作目录
- `.git/` 在根目录下
- 可以直接编辑文件

### 裸仓库 (Bare)
- 没有工作目录
- 直接是 `.git/` 的内容
- 常用于服务器端

##  BaseRepo vs Repo

### BaseRepo（抽象基类）
- 定义仓库接口
- 不依赖具体实现

### Repo（磁盘仓库）
- 基于文件系统的实现
- 继承自 BaseRepo

##  代码示例

### 打开仓库
```python
# TODO: 补充代码示例
```

### 获取对象
```python
# TODO: 补充代码示例
```

### 获取引用
```python
# TODO: 补充代码示例
```

### 读取配置
```python
# TODO: 补充代码示例
```

##  关键实现细节

### 仓库发现机制
如何从子目录找到 `.git/`？

### 配置优先级
1. `.git/config` (仓库级)
2. `~/.gitconfig` (用户级)
3. `/etc/gitconfig` (系统级)

### 上下文管理器
`with Repo(".") as repo:` 的实现原理

##  思考题

1. 为什么需要 `BaseRepo` 抽象基类？
2. 裸仓库和普通仓库的使用场景有什么区别？
3. `Repo` 对象如何保证线程安全？
4. 如何实现 `git worktree` 功能？

---

**下一步**：学习 [引用系统](refs.md)，了解分支和标签的实现。

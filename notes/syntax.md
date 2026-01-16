## NewType

from typing import NewType

## Argparse

### 2. **argparse 使用技巧**

#### 技巧 1：`parse_known_args()`

用于两阶段解析，先处理全局选项，再传递给子命令。

#### 技巧 2：`nargs` 参数

```python
# "+" 表示至少一个参数
parser.add_argument("path", nargs="+")

# "?" 表示可选参数
parser.add_argument("committish", nargs="?")

# "*" 表示零个或多个
parser.add_argument("files", nargs="*")
```

#### 技巧 3：`choices` 限制

```python
parser.add_argument(
    "--objectformat",
    choices=["sha1", "sha256"],  # 只接受这两个值
)
```

#### 技巧 4：`action="store_true"`

```python
parser.add_argument("--bare", action="store_true")
# 如果指定了 --bare，parsed_args.bare 就是 True
```

#### 技巧 5：`add_help=False`

```python
parser = argparse.ArgumentParser(add_help=False)
# 自己处理 --help，而不是让 argparse 自动处理
```

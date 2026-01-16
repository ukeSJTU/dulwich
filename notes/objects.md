# Git 对象模型

> 源文件：`dulwich/objects.py`

## 学习目标

理解 Git 的四种核心对象类型及其在文件系统中的存储方式。

## 四种对象类型

### 1. Blob（二进制大对象）

-   **作用**：存储文件内容
-   **特点**：
-   **存储位置**：
-   **SHA-1 计算**：

### 2. Tree（树对象）

-   **作用**：表示目录结构
-   **特点**：
-   **包含内容**：
-   **Tree Entry 格式**：

### 3. Commit（提交对象）

-   **作用**：表示一次提交
-   **包含内容**：
    -   Tree SHA（快照）
    -   Parent SHA（父提交）
    -   Author（作者）
    -   Committer（提交者）
    -   Message（提交信息）
-   **特点**：

### 4. Tag（标签对象）

-   **作用**：给特定对象打标签
-   **类型**：
    -   轻量标签（lightweight）
    -   附注标签（annotated）
-   **包含内容**：

## ShaFile 基类

### 作用

所有 Git 对象的基类，提供通用功能。

### 核心方法

-   `sha()` - 计算对象的 SHA-1
-   `as_raw_string()` - 序列化为字节串
-   `from_raw_string()` - 从字节串反序列化
-   `type_name` - 对象类型名称

### 对象格式

```
<type> <size>\0<content>
```

## 关键实现细节

### SHA-1 计算流程

TODO: 补充

### 对象序列化格式

TODO: 补充

### 对象之间的引用关系

```
Commit → Tree → Blob
       ↓
     Parent Commit
```

## 代码示例

### 创建 Blob 对象

```python
# TODO: 补充代码示例
```

### 创建 Tree 对象

```python
# TODO: 补充代码示例
```

### 创建 Commit 对象

```python
# TODO: 补充代码示例
```

## 思考题

1. 为什么 Git 不直接存储文件名和路径？
2. Blob 对象如何实现内容去重？
3. Commit 对象为什么需要同时记录 author 和 committer？
4. Tree 对象如何表示空目录？

---

**下一步**：学习 [对象存储](object-store.md)，了解这些对象如何持久化到磁盘。

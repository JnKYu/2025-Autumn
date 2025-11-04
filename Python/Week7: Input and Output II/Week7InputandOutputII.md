# Week7: Input and Output II

## 🧭 课程主题

**CS112: Introduction to Python Programming**
**Week 7：Input and Output II（输入与输出 II）**

---

## 🗓️ 课程安排

* **Assignment 2：Flow Control** — 截止 10月27日 16:00
* **Assignment 3：Input and Output** — 截止 11月9日 16:00
* **Quiz 2：Flow Control, Input and Output** — Week 9 Lab（11月7日）

---

## 📚 主要内容大纲

### 一、Files（文件基础）

1. **文件命名规则**

   * 文件名 = 基础名称 + 可选扩展名（`.` 分隔）
   * 示例：`assignments.docx`, `data.csv`
   * 扩展名通常表示文件类型，但更改扩展名不会改变文件内容

2. **目录与路径（Directories and Paths）**

   * 目录（directory）：存储文件的位置
   * 路径（path）：从根目录到文件的完整名称列表
   * 文件系统结构呈树状

3. **绝对路径与相对路径（Absolute & Relative Paths）**

   * **绝对路径**：从根开始的完整路径
   * **相对路径**：相对于当前工作目录的路径
   * 示例：

     * 绝对路径 `/Users/davidgries/Work/CS2110Spring2017/TAs`
     * 相对路径 `./CS2110Spring2017/TAs`

---

### 二、Handling Files（文件操作）

1. **文件的基本操作流程**

   * 从文件读取数据 → 程序处理 → 写入新文件

2. **Reading Files（读取文件）**

   * 三个步骤：

     1. **打开文件**：`open(file, mode)`
     2. **读取内容**：`read()`、`readline()`、`readlines()`
     3. **关闭文件**：`file.close()` 或使用 `with` 自动关闭

   * **常见模式（mode）**：

     * `'r'`：只读（默认）
     * `'w'`：只写（覆盖原文件）
     * `'a'`：追加写入
     * `'r+'`：读写（文件必须存在）
     * `'a+'`：追加+读（不存在则创建）
     * `'w+'`：读写（存在则覆盖）
     * `'rb'` / `'wb'`：以二进制方式读写

   * **读取方法**：

     * `read(n)`：读取 n 字节
     * `readline()`：读取一行
     * `readlines()`：按行读取成列表
     * `str.strip()` / `str.rstrip()`：去除多余空白符

   * **with语句**：自动管理文件关闭

     ```python
     with open("file.txt", "r") as f:
         for line in f:
             print(line)
     ```

---

### 三、Common Text File Formats（常见文本文件格式）

1. **Plain Text (.txt)**：普通文本文件
2. **Tab-delimited / TSV 文件 (.txt / .tsv)**

   * 用 `\t`（制表符）分隔数据
3. **CSV 文件 (.csv)**

   * 逗号分隔数据（Comma Separated Values）
   * 最常用于电子表格和数据库
   * 可使用 `for line in file:` 直接遍历

---

### 四、Writing Files（写入文件）

1. **基本流程**

   * Step 1. 打开文件（模式 `'w'` 或 `'a'`）
   * Step 2. 写入数据：

     * `file.write(string)`
     * `file.writelines(list)`（不会自动换行）
   * Step 3. 关闭文件：`file.close()` 或 `with`

2. **写入分隔文件**

   * **CSV 文件**：用 `,` 分隔
   * **TSV 文件**：用 `\t` 分隔

---

### 五、csv 模块（处理CSV文件）

1. **读取 CSV 文件**

   ```python
   import csv
   with open("data.csv") as f:
       reader = csv.reader(f)
       for row in reader:
           print(row)
   ```

   * `csv.reader(csvfile)`：返回一个迭代器，每行返回字符串列表
   * `next(iterator)`：读取下一行

2. **使用 DictReader 读取**

   ```python
   import csv
   with open("data.csv") as f:
       reader = csv.DictReader(f)
       for row in reader:
           print(row["Name"])
   ```

   * `fieldnames` 参数可自定义键名

3. **写入 CSV 文件**

   ```python
   with open("data.csv", "w", newline="") as f:
       writer = csv.writer(f)
       writer.writerow(["Name", "Age"])
       writer.writerows([["Alice", 20], ["Bob", 25]])
   ```

---

### 六、Pickle 模块（对象序列化）

1. **功能**

   * 将Python对象保存为二进制格式
   * 用于永久存储或网络传输
   * 支持类型：bool、int、float、str、tuple、list、set、dict

2. **pickle.dump()** — 序列化写入

   ```python
   import pickle
   data = {"name": "Alice", "age": 20}
   with open("data.pkl", "wb") as f:
       pickle.dump(data, f)
   ```

3. **pickle.load()** — 反序列化读取

   ```python
   with open("data.pkl", "rb") as f:
       result = pickle.load(f)
       print(result)
   ```

---

### 七、Code Modularization（代码模块化）

1. **概念**

   * 提高代码复用性与可读性
   * Python模块化方式：函数（functions）、模块（modules）、包（packages）、类（classes）

2. **Functions（函数）**

   * **定义函数**：`def function_name(params):`
   * **命名规范**：使用小写字母和下划线（PEP8）
   * **参数与返回值**：

     * 可接受任意类型参数（数值、字符串、列表等）
     * 可返回单一或多个值（默认以tuple形式）
   * **文档字符串（Docstring）**：

     ```python
     def square(x):
         """Return the square of x."""
         return x ** 2
     ```
   * **调用函数**：`function_name(arguments)`
   * **无返回值函数**：自动返回 `None`

---

✅ **总结**
Week 7 主要内容是 **文件操作进阶** 与 **代码模块化**：

* 文件路径、模式与读写方法
* CSV 与 Pickle 文件处理
* 函数与模块化思想

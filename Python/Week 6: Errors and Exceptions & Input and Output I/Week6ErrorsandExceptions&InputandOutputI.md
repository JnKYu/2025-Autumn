## Week 6: Errors and Exceptions & Input and Output I

### 🧭 课程主题

**Errors and Exceptions（错误与异常） & Input and Output I（输入输出 I）**

---

### 🗓️ 课程安排

* **Assignment 2** 截止：10月24日（Week 7 前）
* **Quiz 2**：Errors and Exceptions, I/O
* **Lab**：今日（实践题，40分钟）

---

### 📚 主要内容大纲

#### 一、错误与异常（Errors and Exceptions）

1. **错误类型（Error Types）**

   * 常见错误：`NameError`、`TypeError` 等
   * 官方异常类型列表【链接】（[https://docs.python.org/3.6/library/exceptions.html）](https://docs.python.org/3.6/library/exceptions.html）)

2. **抛出异常（Raise Exceptions）**

   * 使用 `raise` 主动触发错误
   * 自定义异常类型及错误信息

3. **捕获异常（Catching Exceptions）**

   * 使用 `try ... except ... else ... finally` 结构
   * 捕获不同类型的异常
   * `else`：无异常时执行的代码
   * `finally`：无论是否发生异常都执行的代码

4. **异常处理示例**

   * 处理 `ZeroDivisionError` 和 `FileNotFoundError`
   * 捕获多个异常类型

---

#### 二、输入输出（Input and Output）

1. **输入与输出简介（Introduction to I/O）**

   * **输入（Input）**：从用户或文件接收数据
   * **输出（Output）**：向用户或文件输出数据

2. **键盘输入（Keyboard Input）**

   * 使用 `input()` 函数获取用户输入
   * 输入始终为字符串类型（`str`）
   * 可选的输入提示信息（prompt）

3. **屏幕输出（Screen Output）**

   * 使用 `print()` 函数进行输出
   * **格式化输出**：

     * 使用 `str.format()`
     * 使用 f-strings（f"..."）

4. **文件输入输出（File I/O）**

   * **文本文件**：存储字符数据，使用ASCII或Unicode编码（默认UTF-8）
   * **二进制文件**：存储原始二进制数据
   * **文件操作**：使用 `open()` 打开文件、读取和写入文件

     * 常见文件模式：`'r'`、`'w'`、`'a'`
     * 使用 `read()`、`readline()`、`readlines()` 读取文件内容

5. **文件路径与操作（File Paths and Operations）**

   * 绝对路径与相对路径
   * 使用 `os` 模块进行目录操作：

     * `os.getcwd()` 获取当前工作目录
     * `os.chdir(path)` 更改工作目录
     * `os.remove(file)` 删除文件
     * `os.rename(src, dst)` 重命名文件

---

#### 三、文件格式（File Formats）

1. **常见文本文件格式**

   * **CSV文件**：逗号分隔值格式
   * **TSV文件**：制表符分隔格式
   * **FASTA格式**：用于存储生物数据（如DNA、蛋白质序列）

2. **Pickle模块**

   * **序列化与反序列化**：

     * `pickle.dump()` 将Python对象转换为字节流存储
     * `pickle.load()` 从字节流中恢复Python对象

---

#### 四、文件读取与写入（Reading and Writing Files）

1. **读取文件**

   * `open(file, mode)`：打开文件
   * 使用 `read()`、`readline()`、`readlines()` 读取文件
   * 关闭文件：`file.close()` 或使用 `with` 语句自动关闭

2. **写入文件**

   * `file.write()` 写入数据
   * **追加模式（`'a'`）**：向文件末尾添加内容
   * 使用 `with open(file, 'w') as f` 写入并自动关闭文件

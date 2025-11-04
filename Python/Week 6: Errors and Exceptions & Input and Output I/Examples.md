### 一、错误与异常（Errors and Exceptions）

#### 1. 错误类型（Error Types）

* **`ValueError` 示例**:

```python
# 内置函数接收到无法转换的字符串会抛出 ValueError
int("abc")  # ValueError: invalid literal for int() with base 10: 'abc'
```

* **`NameError` 示例**:

```python
# 访问未定义的变量会抛出 NameError
print(x)  # NameError: name 'x' is not defined
```

* **`TypeError` 示例**:

```python
# 尝试将字符串与整数相加会抛出 TypeError
result = "Hello" + 5  # TypeError: can only concatenate str (not "int") to str
```


#### 2. 抛出异常（Raise Exceptions）

```python
# 使用 raise 手动抛出异常
def check_positive(num):
    if num < 0:
        raise ValueError("Input must be a positive number.")
    return num

try:
    check_positive(-1)
except ValueError as e:
    print(e)  # 输出: Input must be a positive number.
```

#### 3. 捕获异常（Catching Exceptions）

```python
# 使用 try-except 结构捕获异常
try:
    num = int(input("请输入一个数字: "))
    print(f"你输入的数字是: {num}")
except ValueError:
    print("输入无效，请输入一个数字！")
finally:
    print("程序结束。")
```

---

### 二、输入输出（Input and Output）

#### 1. 键盘输入（Keyboard Input）

```python
# 使用 input() 获取用户输入
name = input("请输入你的名字: ")
print(f"你好，{name}!")
```

#### 2. 屏幕输出（Screen Output）

```python
# 使用 print() 打印输出
country = "中国"
print(f"我住在{country}")  # 使用 f-string 格式化输出
```

#### 3. 文件输入输出（File I/O）

##### 1. 文件写入（Writing to File）

```python
# 将内容写入文件
with open("output.txt", "w") as f:
    f.write("这是一个测试文件。\n")
    f.write("写入了第二行内容。")
```

##### 2. 文件读取（Reading from File）

```python
# 读取文件内容
with open("output.txt", "r") as f:
    content = f.read()
    print(content)  # 输出文件内容
```

---

### 三、文件格式（File Formats）

#### 1. CSV文件（CSV Format）

```python
import csv

# 写入CSV文件
with open("data.csv", mode="w", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["姓名", "年龄"])
    writer.writerow(["张三", 25])
    writer.writerow(["李四", 30])

# 读取CSV文件
with open("data.csv", mode="r") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)  # 输出每一行
```

#### 2. Pickle模块（Pickle）

```python
import pickle

# 序列化（将Python对象存储为二进制数据）
data = {"name": "张三", "age": 25}
with open("data.pkl", "wb") as f:
    pickle.dump(data, f)

# 反序列化（从文件中读取Python对象）
with open("data.pkl", "rb") as f:
    loaded_data = pickle.load(f)
    print(loaded_data)  # 输出: {'name': '张三', 'age': 25}
```

---

### 四、文件读取与写入（Reading and Writing Files）

#### 1. 读取文件（Reading from File）

```python
# 打开文件并读取内容
with open("sample.txt", "r") as file:
    content = file.read()
    print(content)  # 输出文件内容
```

#### 2. 写入文件（Writing to File）

```python
# 写入内容到文件
with open("output.txt", "w") as file:
    file.write("这是写入的第一行。\n")
    file.write("这是写入的第二行。")
```

#### 3. 使用`with`语句自动关闭文件（Using `with` to Auto Close Files）

```python
# 使用 with 语句自动关闭文件
with open("output.txt", "a") as file:
    file.write("这是追加的一行。")  # 自动关闭文件
```

## 一、Files（文件基础）

### 1) 文件命名与扩展名

```python
filename = "data.csv"           # 基名+扩展名
print(filename.split("."))      # ['data', 'csv']
```

### 2) 目录与路径（tree & path）

```python
import os
print(os.getcwd())                       # 当前工作目录
print(os.path.join("data", "codon.csv")) # 拼路径，跨平台安全
```

### 3) 绝对路径 vs 相对路径

```python
import os
abs_path = os.path.abspath("data/codon.csv")  # 绝对路径
rel_path = "./data/codon.csv"                 # 相对路径
print(abs_path, rel_path)
```

---

## 二、Handling Files（文件操作）

### 1) 读取文件 3 步（open → read → close）

```python
# 准备一个小文件
with open("demo.txt", "w", encoding="utf-8") as f:
    f.write("line1\nline2\n")

# 传统方式
f = open("demo.txt", "r", encoding="utf-8")
content = f.read()
f.close()
print(content)
```

### 2) 常见 mode（'r'/'w'/'a'/'rb'/'wb' 等）

```python
# 覆盖写入（w）
with open("modes.txt", "w", encoding="utf-8") as f:
    f.write("first\n")
# 追加写入（a）
with open("modes.txt", "a", encoding="utf-8") as f:
    f.write("second\n")
# 二进制写入（wb）
with open("bin.dat", "wb") as f:
    f.write(bytes([0, 1, 2, 255]))
```

### 3) read / readline / readlines

```python
with open("demo.txt", "r", encoding="utf-8") as f:
    print("read(5):", f.read(5))       # 读 5 个字符
with open("demo.txt", "r", encoding="utf-8") as f:
    print("readline():", f.readline().rstrip())
with open("demo.txt", "r", encoding="utf-8") as f:
    print("readlines():", [line.strip() for line in f.readlines()])
```

### 4) strip / rstrip 清理空白

```python
s = "  hello \n"
print(s.strip())   # "hello"
print(s.rstrip())  # "  hello"
```

### 5) with 自动关闭

```python
with open("with.txt", "w", encoding="utf-8") as f:
    f.write("auto close")
# 到这里文件已自动关闭
```

---

## 三、Common Text File Formats（常见文本格式）

### 1) Plain Text（.txt）

```python
with open("plain.txt", "w", encoding="utf-8") as f:
    f.write("a b c\n1 2 3")
with open("plain.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip().split())  # 简单按空白切分成“表格”
```

### 2) TSV（tab 分隔 .tsv）

```python
rows = [["codon", "aa"], ["UUU", "F"], ["UUA", "L"]]
with open("table.tsv", "w", encoding="utf-8") as f:
    for r in rows:
        f.write("\t".join(r) + "\n")
with open("table.tsv", "r", encoding="utf-8") as f:
    for line in f:
        print(line.rstrip("\n").split("\t"))
```

### 3) CSV（逗号分隔 .csv）

```python
with open("table.csv", "w", encoding="utf-8") as f:
    f.write("codon,aa\nUUU,F\nUUA,L\n")
with open("table.csv", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip().split(","))  # 手动解析（后面会用 csv 模块）
```

---

## 四、Writing Files（写文件）

### 1) write / writelines（注意不自动换行）

```python
with open("write_demo.txt", "w", encoding="utf-8") as f:
    f.write("lineA\n")                 # 手动加 \n
    f.writelines(["lineB\n", "lineC\n"])
```

### 2) 写 CSV / TSV

```python
# CSV
with open("out.csv", "w", encoding="utf-8", newline="") as f:
    f.write("name,age\nAlice,20\nBob,25\n")
# TSV
with open("out.tsv", "w", encoding="utf-8") as f:
    f.write("name\tage\nAlice\t20\nBob\t25\n")
```

---

## 五、csv 模块

### 1) csv.reader 读取

```python
import csv

with open("table.csv", "r", encoding="utf-8") as f:
    reader = csv.reader(f)
    for row in reader:
        print("ROW:", row)
```

### 2) next(iterator) 取下一行

```python
import csv

with open("table.csv", "r", encoding="utf-8") as f:
    it = csv.reader(f)
    header = next(it)      # 读表头
    print("HEADER:", header)
    first = next(it)       # 读第一行数据
    print("FIRST:", first)
```

### 3) DictReader（字典形式）

```python
import csv

with open("table.csv", "r", encoding="utf-8") as f:
    reader = csv.DictReader(f)  # 用首行作为键
    for row in reader:
        print(row["codon"], "->", row["aa"])
```

### 4) csv.writer 写入

```python
import csv

rows = [["name", "age"], ["Alice", 20], ["Bob", 25]]
with open("writer.csv", "w", encoding="utf-8", newline="") as f:
    w = csv.writer(f)
    w.writerows(rows)
```

---

## 六、Pickle（对象序列化）

### 1) dump / load

```python
import pickle

data = {"x": [1, 2, 3], "ok": True}
with open("data.pkl", "wb") as f:
    pickle.dump(data, f)        # 序列化到二进制文件

with open("data.pkl", "rb") as f:
    obj = pickle.load(f)        # 反序列化
print(obj)
```

### 2) ‘wb’/‘rb’ 的必要性（字节流）

```python
import pickle, io

buf = io.BytesIO()
pickle.dump({"a": 1}, buf)  # 必须是“字节”目标
buf.seek(0)
print(pickle.load(buf))
```

---

## 七、Code Modularization & Functions（模块化与函数）

### 1) 定义与调用函数（含 docstring）

```python
def square(x):
    """Return x squared."""
    return x * x

print(square(5))
print(square.__doc__)  # 查看文档字符串
```

### 2) 返回多个值（打包成 tuple）

```python
def stats(a, b):
    s = a + b
    p = a * b
    return s, p  # 返回 (和, 积)

s, p = stats(3, 4)
print(s, p)
```

### 3) 无返回值（隐式返回 None）

```python
def greet(name):
    print(f"Hello, {name}!")

ret = greet("Alice")
print(ret is None)  # True
```

### 4) 参数与一一对应

```python
def area(w, h):
    return w * h

print(area(3, 5))            # 位置参数
print(area(h=5, w=3))        # 关键字参数
```

---

如果你希望，我可以把这些示例打包成一个可运行的 `.py` 文件，或拆成按章节的 Jupyter Notebook 版本，方便你逐段运行与标注。

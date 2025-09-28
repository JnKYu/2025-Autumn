# 一、数据集合（Lists / Tuples / Sets / Dictionaries）

```python
# 列表（List） — 有序、可重复、可修改
fruits = ["apple", "banana", "orange"]
fruits.append("pear")         # 添加
fruits.insert(1, "kiwi")      # 在索引1处插入
print(fruits)                 # ['apple', 'kiwi', 'banana', 'orange', 'pear']
print(fruits[2])              # 通过索引访问 -> 'banana'
fruits.remove("kiwi")         # 按值删除
print(fruits.pop())           # 弹出并返回最后一个元素 'pear'
print("banana" in fruits)     # 成员检查 -> True
fruits.sort()                 # 原地排序
print(fruits)
```

```python
# 元组（Tuple） — 有序、不可修改
point = (3, 4)
x, y = point                  # 可以解包
print("x=", x, "y=", y)
# point[0] = 5   # 会报错：TypeError，因为元组不可变
print(point.count(3))         # 统计出现次数
print(point.index(4))         # 查找元素索引
```

```python
# 集合（Set） — 无序、不重复
a = {1, 2, 3, 3}
b = set([3, 4, 5])
print(a)                      # {1,2,3}，自动去重
a.add(6)
a.discard(2)                  # 如果不存在不会报错
print(a.union(b))             # 并集
print(a.intersection(b))      # 交集
print(a.difference(b))        # 差集：在 a 但不在 b
```

```python
# 字典（Dictionary） — 键值对、无序（Python 3.7+ 在实现上保留插入顺序但语义上按键访问）
student = {"id": 1001, "name": "Alice", "scores": [90, 85, 88]}
print(student["name"])        # 通过键访问 -> 'Alice'
print(student.get("age", 18)) # get 提供默认值 -> 18
student["age"] = 20           # 新增或更新
student.update({"major": "CS", "id": 1002})  # 批量更新（id 会被覆盖）
print(list(student.keys()))   # keys 列表
print(list(student.values())) # values 列表
print(list(student.items()))  # items 列表 (键值对元组)
del student["major"]          # 删除键
print("id" in student)        # 键存在检查
```

# 二、各数据类型及常用操作（int, float, bool, str）

```python
# 整数与浮点
a = int("42")
b = float("3.14")
print(a + 10)                 # 52
print(round(b, 1))            # 3.1 四舍五入

# 布尔
print(bool(0), bool(1))       # False True
print((3 > 2) and (2 > 1))    # True，逻辑运算

# 字符串（不可变）及常用方法
s = "  Hello, world!  "
print(len(s))
parts = s.strip().split(",")  # strip 去两端空白，split 分割
print(parts)                  # ['Hello', ' world!']
joined = " & ".join(["A", "B", "C"])
print(joined)                 # 'A & B & C'
print(s.lower(), s.upper())
print(s.replace("world", "Python"))
print(s.startswith("  He"))   # True
print(s.endswith("!  "))      # True
```

# 三、列表 / 元组 / 集合 / 字典 的常用方法小结（带示例）

```python
# 列表方法示例
L = [3, 1, 4, 1, 5]
L.append(9)
L.extend([2, 6])
print(L.count(1))     # 出现次数
print(L.index(4))     # 元素索引（第一个）
L.sort()              # 原地排序
L.reverse()
print(L.pop(0))       # 弹出并返回索引元素

# 元组（不可变）常用
t = (1,2,3,2)
print(t.count(2))
print(t.index(3))

# 集合方法示例
s1 = {1,2,3}
s2 = {3,4}
s1.add(5)
s1.remove(1)
print(s1.isdisjoint(s2))   # 是否没有交集

# 字典方法示例（补充）
d = {}
d.update([("a", 1), ("b", 2)])  # 用可迭代对象更新
print(d.pop("a"))               # 返回并移除键
# d.pop("x")  # KeyError，如果不确定可用 d.pop("x", default_value)
```

# 四、数据类型比较（示例说明何时用哪个）

```python
# 列表 vs 元组：需要修改用列表，不需要修改且想作为 dict 的键或保护不被改动可用元组
coords_list = [0, 0]
coords_tuple = (0, 0)

# 列表 vs 集合：需保序或允许重复用列表；需去重或集合运算用集合
names = ["Alice", "Bob", "Alice"]
unique_names = set(names)

# 字典 vs 列表：需要通过键快速访问时用字典，通过索引顺序访问用列表
users = [{"id":1, "name":"A"}, {"id":2, "name":"B"}]    # 列表+字典混合使用（常见）
users_by_id = {u["id"]: u for u in users}              # 字典索引查找更快
print(users_by_id[2])
```

# 五、流程控制（if / if-else / if-elif-else / 嵌套 if）

```python
# 单分支 if
x = -5
if x < 0:
    print("x 是负数")

# if-else 双分支
n = 7
if n % 2 == 0:
    print("偶数")
else:
    print("奇数")

# if-elif-else 多分支
score = 78
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "D"
print("等级：", grade)

# 嵌套 if
age = 20
if age >= 18:
    if age >= 21:
        print("成年人并且可以饮酒（按某些国家/地区规则）")
    else:
        print("成年人但年龄 <21")
else:
    print("未成年人")
```

# 六、缩进与逻辑运算符（示例）

```python
# 缩进示例（推荐使用4个空格）
a = 10
if a > 0:
    print("正数")
    if a % 2 == 0:
        print("且为偶数")

# 逻辑运算符示例
x, y = 5, 8
if x < 10 and y > 5:
    print("两个条件都成立")
if x < 10 or y < 5:
    print("至少一个条件成立")
if not (x == y):
    print("x 不等于 y")
```

# 七、字符串的 split / join / strip / replace 快速示例

```python
s = "apple,banana,orange"
lst = s.split(",")           # ['apple', 'banana', 'orange']
s2 = "-".join(lst)           # 'apple-banana-orange'
s3 = "  abc  ".strip()       # 'abc'
s4 = "aaa bbb aaa".replace("aaa", "xxx")
print(lst, s2, s3, s4)
```

# 八、字典的进阶用法（从序列创建、可哈希键、遍历）

```python
# 从序列创建字典
pairs = [("a", 1), ("b", 2)]
d = dict(pairs)
print(d)

# 可哈希键：只有不可变对象可作键
good_key = (1,2)
# bad_key = [1,2]  # 不能作为字典键（会报 TypeError）

# 遍历字典
for k, v in d.items():
    print(k, v)

# 字典推导式（快速创建）
squares = {i: i*i for i in range(5)}
print(squares)   # {0:0, 1:1, 2:4, ...}
```

# 九、练习建议（快速上手练习题）

1. 写一个函数，接收一串以逗号分隔的名字，返回去重并按字母排序后的列表。
2. 给一个整数列表，返回一个字典：键为整数，值为该整数在列表中出现的次数。
3. 写一个程序，判断给定字符串是否为回文（忽略空格与大小写）。

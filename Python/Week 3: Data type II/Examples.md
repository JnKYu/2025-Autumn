# List（列表）

### 1) 创建与基本特性（有序、可包含不同类型、可重复）

```python
lst = [1, "a", 1.5, True, 1]
print(lst)  # [1, 'a', 1.5, True, 1]
```

### 2) 索引与切片

```python
lst = [10, 20, 30, 40, 50]
print(lst[0], lst[-1])        # 10 50
print(lst[1:4])               # [20, 30, 40]
print(lst[:3], lst[::2])      # [10, 20, 30] [10, 30, 50]
```

### 3) 嵌套列表与多级索引

```python
grid = [[1, 2], [3, 4, 5], [6]]
print(grid[1][2])  # 5
```

### 4) 拼接与重复（`+`、`*`）

```python
a = [1, 2]
b = [3, 4]
print(a + b)   # [1, 2, 3, 4]
print(a * 3)   # [1, 2, 1, 2, 1, 2]
```

### 5) 可变性：增删改

```python
nums = [10, 20, 30]
nums.append(40)              # 末尾加
nums.insert(1, 15)           # 指定位置加
nums[2] = 25                 # 修改
print(nums)                  # [10, 15, 25, 30, 40]

nums.remove(25)              # 按值删（只删第一个）
popped = nums.pop()          # 默认删末尾并返回
del nums[0]                  # 按索引删
print(nums, popped)          # [15, 30] 40
```

### 6) 赋值是“引用”不是拷贝（别名问题）

```python
a = [1, 2, 3]
b = a            # b 和 a 指向同一对象
b.append(4)
print(a, b)      # [1, 2, 3, 4] [1, 2, 3, 4]

# 正确拷贝：切片或 list()
c = a[:]         # 或 c = list(a) / copy.copy(a) / deepcopy
c.append(5)
print(a, c)      # [1, 2, 3, 4] [1, 2, 3, 4, 5]
```

### 7) `del` 删除切片或清空

```python
x = [0, 1, 2, 3, 4, 5]
del x[1:4]
print(x)   # [0, 4, 5]
del x[:]   # 清空
print(x)   # []
```

### 8) 内置函数：`len/sum/max/min`

```python
vals = [3, 1, 4, 1, 5]
print(len(vals), sum(vals), max(vals), min(vals))  # 5 14 5 1
```

### 9) 排序：`sorted()` vs `list.sort()`

```python
s = [3, 1, 4, 1, 5]
print(sorted(s))   # 返回新列表 [1, 1, 3, 4, 5]
print(s)           # 原列表不变 [3, 1, 4, 1, 5]
s.sort(reverse=True)
print(s)           # 就地排序 [5, 4, 3, 1, 1]
```

### 10) 常用方法：`append/insert/pop/remove/count/index/sort(key=...)`

```python
words = ["apple", "banana", "apple", "cherry"]
print(words.count("apple"))          # 2
print(words.index("banana"))         # 1
words.remove("apple")                # 只移除第一个 apple
p = words.pop(1)                     # 移除并返回索引1元素
print(words, p)                      # ['banana', 'cherry'] 'banana'

pairs = ["10", "2", "1"]
pairs.sort(key=int)                  # 自定义排序键
print(pairs)                         # ['1', '2', '10']
```

---

# Tuple（元组）

### 1) 创建与不可变性

```python
t = (1, "a", 3.14)
print(t)         # (1, 'a', 3.14)
# t[0] = 99      # ❌ TypeError: 元组不可修改
```

### 2) 索引与切片

```python
t = (10, 20, 30, 40, 50)
print(t[0], t[-1])    # 10 50
print(t[1:4])         # (20, 30, 40)
```

### 3) 拼接、重复、成员检测

```python
a = (1, 2)
b = (3,)
print(a + b)     # (1, 2, 3)
print(a * 3)     # (1, 2, 1, 2, 1, 2)
print(2 in a)    # True
```

### 4) 内置函数与方法：`len/sum/max/min/sorted`、`count/index`

```python
nums = (3, 1, 4, 1, 5)
print(len(nums), sum(nums), max(nums), min(nums))  # 5 14 5 1
print(sorted(nums))       # [1, 1, 3, 4, 5]（返回列表）
print(nums.count(1))      # 2
print(nums.index(4))      # 2
```

### 5) 打包与解包（Packing & Unpacking）

```python
# 打包
p = ("Alice", 20, "CS")
# 解包
name, age, major = p
print(name, age, major)   # Alice 20 CS

# 带“星号解包”
a, *mid, b = (1, 2, 3, 4, 5)
print(a, mid, b)          # 1 [2, 3, 4] 5
```

### 6) `zip()` 将序列配对成元组迭代器

```python
names = ["A", "B", "C"]
scores = [90, 85, 88]
for name, score in zip(names, scores):
    print(name, score)
# A 90
# B 85
# C 88
```

---

# Set（集合）

### 1) 创建与基本特性（无序、元素唯一、仅包含不可变对象）

```python
s = {1, 2, 2, 3}
print(s)         # {1, 2, 3}  （自动去重）
print(len(s))    # 3
print(2 in s)    # True
```

### 2) 不能索引，但可遍历

```python
s = {"a", "b", "c"}
for ch in s:
    print(ch)    # 顺序不保证
```

### 3) 集合运算：交/并/差/对称差

```python
A = {1, 2, 3}
B = {3, 4, 5}
print(A & B)     # 交集 {3}
print(A | B)     # 并集 {1, 2, 3, 4, 5}
print(A - B)     # 差集 {1, 2}
print(A ^ B)     # 对称差 {1, 2, 4, 5}
```

### 4) 常用方法：`add/remove/discard`（`remove` 不存在会报错，`discard` 不会）

```python
s = {1, 2}
s.add(3)           # {1, 2, 3}
s.discard(4)       # 没有 4 也不报错
# s.remove(4)      # ❌ KeyError
print(s)
```

### 5) 去重：列表 ↔ 集合

```python
lst = [1, 2, 2, 3, 3, 3]
unique = list(set(lst))
print(unique)      # [1, 2, 3]（顺序不定）

# 如果要“去重但保持原顺序”：
seen, ordered_unique = set(), []
for x in lst:
    if x not in seen:
        seen.add(x)
        ordered_unique.append(x)
print(ordered_unique)  # [1, 2, 3]
```

### 6) 字符串 ↔ 集合（快速拿到唯一字符/去重）

```python
s = "banana"
print(set(s))        # {'b', 'a', 'n'}（无序）
```

### 7) 字符串 ↔ 列表：`split` / `join`

```python
text = "apple,banana,orange"
parts = text.split(",")           # ['apple', 'banana', 'orange']
joined = " | ".join(parts)        # 'apple | banana | orange'
print(parts, joined)
```

### 8) `sorted()` 查看有序视图（集合本身仍无序）

```python
s = {3, 1, 4, 1, 5}
print(sorted(s))     # [1, 3, 4, 5]
```

---

## 速查对比表（一句话记忆）

* **List 列表**：有序、可变、可重复 → 适合需要改动的数据序列
* **Tuple 元组**：有序、不可变、可重复 → 适合“只读、作为字典键或集合元素的组合值”
* **Set 集合**：无序、唯一、可变 → 适合去重与集合运算

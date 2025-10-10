# 1) 条件语句

## 1.1 `if`

```python
x = 7
if x % 2 == 1:
    print("odd")  # 输出: odd
```

## 1.2 `if-else`

```python
score = 62
if score >= 60:
    print("pass")
else:
    print("fail")  # 输出: fail
```

## 1.3 `if-elif-else`

```python
temp = 28
if temp >= 35:
    level = "hot"
elif temp >= 20:
    level = "warm"     # 输出: warm
else:
    level = "cold"
print(level)
```

## 1.4 嵌套条件（nested if）

```python
user = {"role": "admin", "active": True}
if user["active"]:
    if user["role"] == "admin":
        print("show admin panel")  # 输出: show admin panel
    else:
        print("show user panel")
else:
    print("account inactive")
```

---

# 2) 循环（for / while）

## 2.1 `for` 遍历 iterable

```python
for ch in "abc":
    print(ch)  # 逐行输出: a b c
```

## 2.2 `enumerate`

```python
nums = [10, 20, 30]
for i, v in enumerate(nums):
    print(i, v)  # 输出: 0 10 / 1 20 / 2 30
```

## 2.3 `range(start, stop[, step])`

```python
for i in range(2, 10, 3):
    print(i)  # 输出: 2 5 8
```

## 2.4 遍历字典

```python
info = {"name": "Ada", "lang": "Python"}
for k, v in info.items():
    print(k, "=>", v)
# 输出:
# name => Ada
# lang => Python
```

## 2.5 嵌套循环

```python
for i in range(1, 3):
    for j in range(1, 3):
        print(f"{i}x{j}={i*j}", end="; ")
# 输出: 1x1=1; 1x2=2; 2x1=2; 2x2=4;
```

## 2.6 `while` 基本用法 + 防止死循环

```python
n = 0
while n < 5:
    print(n, end=" ")  # 输出: 0 1 2 3 4
    n += 1             # 必须更新条件变量，避免死循环
print()
```

---

# 3) 列表推导式（List Comprehension）

## 3.1 基本形式 + 过滤

```python
nums = [1, 2, 3, 4, 5, 6]
evens = [x for x in nums if x % 2 == 0]
print(evens)  # 输出: [2, 4, 6]
```

## 3.2 带条件表达式

```python
nums = [-2, -1, 0, 1, 2]
transformed = [(-x if x < 0 else x) for x in nums]
print(transformed)  # 输出: [2, 1, 0, 1, 2]
```

## 3.3 文本过滤示例

```python
fruits = ["apple", "pear", "kiwi", "banana"]
with_a = [f for f in fruits if "a" in f]
print(with_a)  # 输出: ['apple', 'pear', 'banana']
```

---

# 4) 循环控制语句：`break` / `continue` / `pass`

## 4.1 `break`（找到第一个能被3整除的数）

```python
nums = [5, 7, 9, 12]
for x in nums:
    if x % 3 == 0:
        print("first divisible by 3:", x)  # 输出: 9
        break
```

## 4.2 `continue`（跳过能被3整除的数）

```python
nums = [3, 4, 5, 6]
for x in nums:
    if x % 3 == 0:
        continue
    print(x, end=" ")  # 输出: 4 5
print()
```

## 4.3 `pass`（占位）

```python
def todo():
    pass  # 将来再实现

for _ in range(3):
    pass  # 语法需要语句，但暂时不做事
```

---

# 5) 循环示例

## 5.1 列表求和（不使用内置 `sum`）

```python
nums = [3, 1, 6, 7, 2]
total = 0
for x in nums:
    total += x
print(total)  # 输出: 19
```

## 5.2 用循环找最大值（不使用内置 `max`）

```python
nums = [3, 1, 6, 7, 2]
maximum = nums[0]
for x in nums[1:]:
    if x > maximum:
        maximum = x
print(maximum)  # 输出: 7
```

## 5.3 冒泡排序（就地排序，演示核心逻辑）

```python
nums = [5, 1, 6, 3, 4]
n = len(nums)
for i in range(n - 1):
    for j in range(n - i - 1):
        if nums[j] > nums[j + 1]:
            nums[j], nums[j + 1] = nums[j + 1], nums[j]
print(nums)  # 输出: [1, 3, 4, 5, 6]
```

---

# 6) 错误与异常

## 6.1 主动抛出异常 `raise`

```python
def sqrt_strict(x):
    if x < 0:
        raise ValueError("x must be non-negative")
    return x ** 0.5

# sqrt_strict(-1)  # 取消注释会抛 ValueError
```

## 6.2 `try / except / else / finally`

```python
def safe_div(a, b):
    try:
        result = a / b
    except ZeroDivisionError as e:
        print("division by zero!", e)
        return None
    except TypeError as e:
        print("type error!", e)
        return None
    else:
        print("ok:", result)   # 仅在没有异常时执行
        return result
    finally:
        print("done")          # 无论如何都会执行

safe_div(10, 2)   # 输出: ok: 5.0 \n done
safe_div(10, 0)   # 输出: division by zero! ... \n done
safe_div(10, "a") # 输出: type error! ... \n done
```

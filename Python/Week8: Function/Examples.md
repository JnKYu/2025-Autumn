
### **1. 代码模块化：**

使用函数来模块化代码，简化管理。

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
```

### **2. 函数（内建函数）**

Python的内建函数 `abs()`、`min()`、`max()` 示例：

```python
# 使用abs()求绝对值
print(abs(-5))  # 输出: 5

# 使用min()和max()找最小值和最大值
numbers = [1, 2, 3, 4, 5]
print(min(numbers))  # 输出: 1
print(max(numbers))  # 输出: 5
```

### **3. 用户定义函数**

自定义一个函数计算数字的平方：

```python
def square(x):
    return x ** 2

print(square(4))  # 输出: 16
```

### **4. 调用函数**

函数调用时传入参数：

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # 输出: 8
```

### **5. 位置参数和关键字参数**

使用位置参数和关键字参数：

```python
def greet(name, age):
    print(f"Hello, {name}! You are {age} years old.")

# 位置参数
greet("Alice", 25)

# 关键字参数
greet(age=25, name="Bob")
```

### **6. 传递可变和不可变对象作为参数**

不可变对象（整数）和可变对象（列表）传递示例：

```python
def modify(x):
    x += 1  # 对整数的修改不会影响外部变量
    return x

a = 5
print(modify(a))  # 输出: 6
print(a)  # 输出: 5 (原始a未改变)

def modify_list(lst):
    lst.append(4)  # 对列表的修改会影响原始列表
    return lst

b = [1, 2, 3]
print(modify_list(b))  # 输出: [1, 2, 3, 4]
print(b)  # 输出: [1, 2, 3, 4] (原始b已改变)
```


### **7. 带默认值的参数**

函数定义带有默认值的参数：

```python
def greet(name, message="Hello"):
    print(f"{message}, {name}!")

greet("Alice")  # 使用默认的 "Hello"
greet("Bob", "Good morning")  # 使用自定义的 "Good morning"
```

### **8. 可变参数（`*args` 和 `**kwargs`）**

传递可变数量的参数：

```python
# *args 示例
def sum_numbers(*args):
    return sum(args)

print(sum_numbers(1, 2, 3, 4))  # 输出: 10

# **kwargs 示例
def greet(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

greet(name="Alice", age=25)  # 输出: name: Alice, age: 25
```

### **9. 命令行参数**

通过命令行传递参数（需在终端执行）：

```python
import sys
print("Command line arguments:", sys.argv)
```

### **10. 变量的作用域和生命周期**

示例展示局部变量和全局变量：

```python
x = 10  # 全局变量

def modify():
    global x  # 使用 global 修改全局变量
    x += 5

modify()
print(x)  # 输出: 15
```

### **11. 递归**

使用递归计算阶乘：

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # 输出: 120
```

### **12. 匿名函数（Lambda表达式）**

使用 `lambda` 函数：

```python
# 用lambda表达式计算两个数的和
sum = lambda a, b: a + b
print(sum(3, 5))  # 输出: 8
```

### **13. 使用 `filter()` 和 `map()`**

使用 `filter()` 过滤列表中的偶数：

```python
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # 输出: [2, 4, 6]
```

使用 `map()` 对列表中的每个元素加倍：

```python
doubled = list(map(lambda x: x * 2, numbers))
print(doubled)  # 输出: [2, 4, 6, 8, 10, 12]
```

### **14. 模块和包**

创建一个简单的模块并导入：

* `mymodule.py`:

```python
def greet(name):
    print(f"Hello, {name}!")
```

* 主程序:

```python
import mymodule
mymodule.greet("Alice")
```

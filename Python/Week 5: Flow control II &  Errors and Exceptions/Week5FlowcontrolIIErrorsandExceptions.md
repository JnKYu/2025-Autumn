### 🧭 课程主题

**Flow Control II（流程控制 II） & Errors and Exceptions（错误与异常）**

---

### 🗓️ 课程安排

* **Assignment 1** 截止：10月17日
* **Quiz 1**：Data Types
* **Lab**：今日（15题，40分钟）
* **Assignment 2**：Flow Control，截止 10月24日（Week 7 前）

---

### 📚 主要内容大纲

#### 一、流程控制（Flow Control）

1. **程序执行流程**

   * 顺序执行（Normal flow）
   * 条件执行（Conditional: `if`）
   * 循环执行（Loop: `for`, `while`）

---

#### 二、条件语句（Conditional Statements）

1. **基本结构**

   * `if`：单条件判断
   * `if-else`：双分支结构
   * `if-elif-else`：多分支结构
   * **嵌套条件语句**（Nested conditionals）

---

#### 三、循环结构（Loops）

1. **循环种类**

   * `for` 循环
   * `while` 循环

2. **for循环细节**

   * 遍历 iterable 对象（list, tuple, string, dict, file 等）
   * `enumerate()` 获取索引和值
   * `range(start, stop[, step])` 生成数列
   * 遍历字典、嵌套循环、更新迭代变量

3. **列表推导式（List Comprehension）**

   * 基本形式：
     `newlist = [expression for item in iterable if condition == True]`
   * 含条件的推导式：
     `[expression1 if condition else expression2 for item in iterable]`
   * 示例：平方计算、过滤含字母"a"的水果、取绝对值等

4. **while循环**

   * 基本结构与逻辑
   * 防止无限循环
   * 示例：打印前10个数字

---

#### 四、循环控制语句（Loop Control Statements）

1. **`break`**：跳出当前循环
2. **`continue`**：跳过当前迭代，继续下一次
3. **`pass`**：空操作，占位符

---

#### 五、循环示例（Examples of Loops）

* 计算列表元素总和
* 找出最大值
* 冒泡排序（Bubble Sort）

  * 双层循环
  * 比较并交换相邻元素

---

#### 六、错误与异常（Errors and Exceptions）

1. **错误类型**

   * 常见错误：`NameError`, `TypeError` 等
   * Python 官方异常列表

2. **抛出异常（Raise Exceptions）**

   * 使用 `raise` 主动触发错误
   * 自定义异常信息

3. **捕获异常（Catching Exceptions）**

   * 使用 `try ... except ... else ... finally` 结构
   * 针对不同异常类型设置多个 `except` 块
   * `finally` 块无论是否发生异常都会执行

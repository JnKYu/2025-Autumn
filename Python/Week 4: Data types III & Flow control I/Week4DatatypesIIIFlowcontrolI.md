# Python课程大纲（第4周）

## 一、课程安排

* 作业1：第5周上课前提交
* 小测1：数据类型（第5周实验课进行）

---

## 二、课程主题

### 1. 数据集合（Data Collections / 数据容器）

* **列表（List）**：有序，可重复，可修改
* **元组（Tuple）**：有序，不可修改
* **集合（Set）**：无序，不重复，可修改
* **字典（Dictionary）**：键值对存储，无序，可修改

---

### 2. 字典（Dictionary）

* **创建字典**：`{key: value}`，或使用 `dict()`
* **键（Key）**：必须是不可变对象，唯一
* **值（Value）**：可为任意对象，可重复
* **索引与访问**：通过键访问 `dict[key]`
* **常用操作**：

  * 添加/更新元素
  * 删除元素 `del`
  * 成员检查：`in` / `not in`
* **常用方法**：

  * `.keys()`、`.values()`、`.items()`
  * `.get(key, default)`
  * `.update({...})`
  * `.pop(key)`、`.popitem()`

---

### 3. Python数据类型复习

* **整型（int）**：加减乘除，`int()` 转换
* **浮点型（float）**：小数，`float()` 转换，`math`库
* **布尔型（bool）**：True / False，逻辑运算符
* **字符串（str）**：不可变，索引与切片

  * 方法：`split()`、`join()`、`strip()`、`replace()`、`startswith()`、`endswith()` 等
* **列表（list）**：可变，有序

  * 方法：`append()`、`extend()`、`insert()`、`remove()`、`pop()`、`sort()`、`reverse()` 等
* **元组（tuple）**：不可变，有序

  * 方法：`len()`、`index()`、`count()`
* **集合（set）**：可变，无序，不重复

  * 方法：`add()`、`remove()`、`discard()`、`union()`、`intersection()`、`difference()`
* **字典（dict）**：键值对，无序

  * 方法：`keys()`、`values()`、`items()`、`get()`、`update()`、`pop()`

---

### 4. 各数据类型比较

* **列表 vs. 元组**：列表可变，元组不可变
* **列表 vs. 集合**：列表有序可重复，集合无序不重复
* **字典 vs. 列表**：字典通过键访问，列表通过索引访问

---

### 5. 流程控制（Flow Control）

* **正常执行**：逐行执行
* **条件语句（if-else）**：

  * `if` 单分支
  * `if-else` 双分支
  * `if-elif-else` 多分支
  * 嵌套条件语句（Nested if）
* **缩进规则**：4个空格，表示代码块

---

👉 总结：本周课程重点是 **字典的使用** 和 **条件语句 if-else 的掌握**，同时复习巩固所有 Python 数据类型。

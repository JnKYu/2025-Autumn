# CS112: Python 程序设计基础

## Week 3: 数据类型 II

### 1. 课程安排

* **作业 1**：本周布置，截止时间第 5 周上课前
* **作业承诺书提交**：第 4 周上课前
* **测验 1（Quiz 1）**：数据类型，第 5 周实验课进行

---

### 2. 数据集合类型（Data Collections）

Python 除了基础数据类型（int, float, bool, str），还提供 **数据容器 (data containers)**：

#### (1) 列表 List

* **特点**：有序，可修改，可包含不同类型元素，可重复
* **表示方法**：`[元素1, 元素2, ...]`
* **操作**：

  * 索引与切片：`list[i]`, `list[start:end:step]`
  * 嵌套列表（多维）
  * 拼接：`+`
  * 重复：`*`
* **可变性**：可增删改元素

  * `append()`, `insert()` 添加元素
  * `pop()`, `remove()`, `del` 删除元素
  * `sort()`, `sorted()` 排序
  * `count()`, `index()` 查询
* **内置函数**：`len()`, `sum()`, `max()`, `min()`

---

#### (2) 元组 Tuple

* **特点**：有序，不可变，类似不可修改的列表
* **表示方法**：`(元素1, 元素2, ...)`
* **操作**：

  * 索引与切片：同列表
  * 拼接：`+`
  * 重复：`*`
  * 成员检测：`in`, `not in`
* **内置函数**：`len()`, `sum()`, `max()`, `min()`, `sorted()`
* **方法**：`count()`, `index()`
* **打包与解包**：Tuple Packing & Unpacking
* **zip() 函数**：将多个序列打包成元组的迭代器

---

#### (3) 集合 Set

* **特点**：无序，元素唯一，只能包含不可变对象
* **表示方法**：`{元素1, 元素2, ...}`
* **常用操作**：

  * 成员检测：`in`, `not in`
  * `len()`, `sorted()`
* **集合运算**：

  * 交集：`&` 或 `.intersection()`
  * 并集：`|` 或 `.union()`
  * 差集：`-` 或 `.difference()`
  * 对称差集：`^` 或 `.symmetric_difference()`
* **方法**：

  * `add()`, `remove()`, `discard()`
* **类型转换**：

  * 列表 ↔ 集合（去重）
  * 字符串 ↔ 集合
  * 字符串 ↔ 列表（`split()`, `join()`）

---

#### (4) 字典 Dictionary （预告）

* **特点**：键值对 (key : value) 的查找表

---

### 3. 更多练习资源

* [列表练习](https://pynative.com/python-list-quiz/)
* [元组练习](https://pynative.com/python-tuple-quiz/)
* [集合练习](https://pynative.com/python-set-quiz/)
* [字符串练习](http://www.coolpython.net/python_primary/data_type/str_exercises.html)

---

⚡ **总结**：
Week 3 的核心是 **三大容器类型**：

* **列表**：有序，可变
* **元组**：有序，不可变
* **集合**：无序，元素唯一

熟悉它们的 **创建方式、常用操作、方法与区别**，是后续学习字典、数据结构和算法的基础。

# 算法学习笔记

## 技巧

- **读入/输出优化：**
  ```cpp
  scanf("%d", &x); // %格式说明符；&取地址，但s不用
  printf("%d", x);
  ```

- **整型读入优化：**

- **快读快写：**
  - 使用 `fread` 或 `mmap` 可以实现更快的读入。

- **分段打表：**
  - 分块思想

- **常见错误：**
  - **CE（编译错误）：** 多为词法、语法和语义错误
  - **WA（答案错误）：** 哈希要使用 `unsigned`

- **常见技巧：**
  - 利用**局部性**
  - **循环宏定义：**
    ```cpp
    #define _rep(i, a, b) for (int i = (a); i <= (b); ++i)
    ```
  - **善用namespace：** 提高程序可读性，便于调试。
  - **使用宏进行调试：**
  - **对拍：**
  - **内存池：**

---

## C++基础

- **`inline` 关键字：**
  在实际应用中主要用于优化小型、频繁调用的函数，尤其是在头文件中定义的函数。合理使用可以提高代码性能，但也需要注意其潜在的缺陷和限制。

- **`std::numeric_limits`（在 `<limits>` 中提供）：**
  从 C++17 起，该类模板用于查询各种算数类型的属性（如最大值、最小值、是否是整形、是否有符号等）。

- **位运算符：**
  - `~`: 逐位非
  - `&`: 逐位与
  - `|`: 逐位或
  - `^`: 逐位异或
  - `<<`: 逐位左移
  - `>>`: 逐位右移

- **运算符：**
  - `<=>`: 三路比较运算符（C++20）

---

## STL容器

- **`vector`:**
  ```cpp
  v0.reserve(3);  // 内存预分配
  ```

- **`array`**
- **`deque`**（双端队列）
- **`list`**（双向链表）
- **`set`**：内部红黑树实现，含有键值类型对象的已排序集，不会出现值相同的元素。
- **`map`**：有序键值对容器，键唯一。`multimap` 中允许多个元素拥有同一键。
- **`stack`**：后进先出（LIFO），只能访问和删除栈顶元素。
- **`queue`**：先进先出（FIFO），只能访问和删除队首元素。
- **`priority_queue`**：优先队列

---

## STL算法

- **`find`**：顺序查找
  ```cpp
  find(v.begin(), v.end(), value);
  ```

- **`reverse`**：翻转数组或字符串
  ```cpp
  reverse(v.begin(), v.end());
  reverse(a + begin, a + end);
  ```

- **`unique`**：去除相邻的重复元素
  ```cpp
  unique(ForwardIterator first, ForwardIterator last);
  ```

- **`sort`**：排序
  ```cpp
  sort(v.begin(), v.end(), cmp);
  sort(a + begin, a + end, cmp);
  ```

- **`stable_sort`**：稳定排序（用法同 `sort()`）

- **`nth_element`**：按指定范围分类，即找出第 n 大的元素
  ```cpp
  nth_element(v.begin(), v.begin() + mid, v.end(), cmp);
  ```

- **`binary_search`**：二分查找
  ```cpp
  binary_search(v.begin(), v.end(), value);
  ```

- **`merge`**：合并两个有序序列
  ```cpp
  merge(v1.begin(), v1.end(), v2.begin(), v2.end(), back_inserter(v3));
  ```

- **`inplace_merge`**：原地合并两个连续范围
  ```cpp
  inplace_merge(v.begin(), v.begin() + middle, v.end());
  ```

- **`lower_bound`**：二分查找第一个 ≥ x 的元素
  ```cpp
  lower_bound(v.begin(), v.end(), x);
  ```

- **`upper_bound`**：二分查找第一个 > x 的元素
  ```cpp
  upper_bound(v.begin(), v.end(), x);
  ```

- **`bitset`**：标准库中存储0/1的固定大小容器，可高效处理二进制位
- **`string`**：
- **`pair`**：
  - 先比较第一个变量，相等时再比较第二个
  - 可以轻松实现离散化
  - pair可作为priority_queue的数据类型(Dijikstra算法的堆优化)
  - map的底层用pair来储存数据(键值对)

---

## C++进阶

- **'类'**：
  - 在实例化变量时设定初始值，需要定义默认构造函数
  - 变量作用范围结束后通过析构函数销毁变量

























      

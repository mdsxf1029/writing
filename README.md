# writing
算法学习笔记
## 技巧：
    · 读入/输出优化：
      scanf("%d", &x); //%格式说明符；&取地址，但s不用
      printf("%d", x);
    · 整型读入优化：
    · 快读快写（板子？）：
      fread/mmap 可以实现更快读入
    · 分段打表：
      分块思想：
    · 常见错误：
      CE：多为词法、语法和语义错误
      WA：哈希要使用unsigned
    · 常见技巧
      利用局部性：
      循环宏定义：
      宏定义简化：
        #define _rep(i, a, b) for (int i = (a); i <= (b); ++i)
      善用namespace：
        使用 namespace 能使程序可读性更好，便于调试。
      使用宏进行调试：
      对拍：
      内存池：
## C++基础：
    · inline 关键字在实际应用中主要用于优化小型、频繁调用的函数，尤其是在头文件中定义的函数。合理使用可以提高代码性能，但也需要注意其潜在的缺陷和限制。
    · C++17 起在 <limits> 中提供了 std::numeric_limits 类模板，用于查询各种算数类型的属性，如最大值、最小值、是否是整形、是否有符号等。
    · 位运算符：
      ~	逐位非
      & （双目）	逐位与
      |	逐位或
      ^	逐位异或
      <<	逐位左移
      >>	逐位右移
    · 运算符：
      <=>	三路比较运算符
    · STL容器：
      vector：
        v0.reserve(3);  //内存预分配
      array：
      deque：  //双端队列
      list：  //双向链表
      set：  //内部红黑树实现，含有键值类型对象的已排序集，不会出现值相同的元素。
      map：  //有序键值对容器，它的元素的键是唯一的。map 中不会存在键相同的元素，multimap 中允许多个元素拥有同一键。
      stack：  //后进后出，只能查删栈顶元素
      queue：  //先进先出，只能查删队首元素
      priority_queue：  //优先队列
    · STL算法：
      find：  //顺序查找。
        find(v.begin(), v.end(), value);  //其中 value 为需要查找的值。
      reverse：  //翻转数组、字符串。
        reverse(v.begin(), v.end());
        reverse(a + begin, a + end);
      unique：  //去除容器中相邻的重复元素。
        unique(ForwardIterator first, ForwardIterator last);
        //返回值为指向去重后容器结尾的迭代器，原容器大小不变。与 sort 结合使用可以实现完整容器去重。
      sort：  //排序。
        sort(v.begin(), v.end(), cmp);
        sort(a + begin, a + end, cmp);
        //其中 end 是排序的数组最后一个元素的后一位，cmp 为自定义的比较函数。
      stable_sort：  //稳定排序，用法同 sort()。
      nth_element：  //按指定范围进行分类，即找出序列中第 n 大的元素，使其左边均为小于它的数，右边均为大于它的数。           nth_element(v.begin(), v.begin() + mid, v.end(), cmp);
        nth_element(a + begin, a + begin + mid, a + end, cmp)。
      binary_search：  //二分查找。
        binary_search(v.begin(), v.end(), value);  //其中 value 为需要查找的值。
      merge：  //将两个（已排序的）序列有序合并到第三个序列的插入迭代器上。
        merge(v1.begin(), v1.end(), v2.begin(), v2.end() ,back_inserter(v3))。
      inplace_merge：  
        inplace_merge(v.begin(), v.begin() + middle, v.end());
        //将两个（已按小于运算符排序的）：[first,middle), [middle,last) 范围原地合并为一个有序序列。
      lower_bound：
        lower_bound(v.begin(),v.end(),x);
        //在一个有序序列中进行二分查找，返回指向第一个大于等于x的元素的位置的迭代器。如果不存在这样的元素，则返回尾迭代器。
      upper_bound：
        upper_bound(v.begin(),v.end(),x);
        //在一个有序序列中进行二分查找，返回指向第一个 大于 x 的元素的位置的迭代器。如果不存在这样的元素，则返回尾迭代器。
      · bitset：  //没懂
        标准库中的一个存储 0/1 的大小不可变容器，可以高效处理二进制位（bit）
      · string：
      · pair：
        pair比较符会先比较第一个变量，相等的话再比较第二个(first\second)
        
      ·



Here's the reformatted version in Chinese, ready for easy copy-pasting into GitHub:

---

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
- **`string`**
- **`pair`**：先比较第一个变量，相等时再比较第二个

---




























      

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

- **类**：
  - 在实例化变量时设定初始值，需要定义默认构造函数
  - 变量作用范围结束后通过析构函数销毁变量
  - `string::at()` 是 `string` 类中的一个成员函数，用于访问字符串中指定位置的字符。与数组下标操作符 `[]` 类似，但 `at()` 会进行边界检查，如果 `n` 超出字符串的范围，会抛出一个 `std::out_of_range` 异常。
  ```cpp
  string s = "hello";
  char &ch = s.at(1);  // ch 是对 'e' 的引用
  ```

- **常值**：
  - `const`：用于声明一个不可修改的变量
  - `constexpr`：要求更严格，要求编译器在编译期间计算常量表达式

---

## 新版C++特性

- **`auto`类型说明符**：用于自动推导变量等的类型

- **基于范围的`for`循环**：冒号前（range_declaration）是每次循环时要操作的变量，可以直接访问或通过引用访问；冒号后（range_expression）是要遍历的范围，比如容器、数组或初始化列表。
  ```cpp
  for (range_declaration : range_expression) loop_statement
  for (int num : numbers)  cout << num << " ";
  ```

- **`lambda`表达式**：

- **`decltype`说明符**：可以推断表达式的类型

- **`std::tuple`**：是固定大小的异类值汇集（在确定初始元素后不能更改，但是初始元素能有任意多个）。它是 `std::pair` 的推广。
  ```cpp
  tuple<int, int, std::string, std::vector<int>> tup = make_tuple(817, 114, "514", vec);
  ```

- **`std::function`**：
  ```cpp
  #include <functional>
  ```

- **可变参数模板**：
  ```cpp
  template <typename T>
  ```

  ---

## 算法基础

- **枚举**：
  - 给出解空间
  - 减少枚举的空间
  - 选择合适的枚举顺序

- **模拟**：
  - 在动手写代码之前，在草纸上尽可能地写好要实现的流程。
  - 在代码中，尽量把每个部分模块化，写成函数、结构体或类。
  - 对于一些可能重复用到的概念，可以统一转化，方便处理：如，某题给你 "YY-MM-DD 时：分" 把它抽取到一个函数，处理成秒，会减少概念混淆。
  - 调试时分块调试。模块化的好处就是可以方便的单独调某一部分。
  - 写代码的时候一定要思路清晰，不要想到什么写什么，要按照落在纸上的步骤写。

- **递归&分治**：
  - 递归(recursion)：在函数的定义中使用函数自身的方法/通过重复将问题分解为同类的子问题而解决问题
    - 特征：结束条件(定义最简子问题的答案)和自我调用(解决子问题)
    - 通过堆栈来实现，递归层数过多时`栈溢出`
    - 递归的优化：`搜索优化`和`记忆化搜索`
  - 分治：分而治之，把复杂问题分成两个或更多的相同或相似的子问题，直到最后子问题可以简单求解
    - 分解 -> 解决 -> 合并(类似二叉树后序遍历模板)
      - 分解原问题为结构相同的子问题。
      - 分解到某个容易求解的边界之后，进行递归求解。
      - 将子问题的解合并成原问题的解。
    - 题型特征：
      - 该问题的规模缩小到一定的程度就可以容易地解决。
      - 该问题可以分解为若干个规模较小的相同问题，即该问题具有最优子结构性质，利用该问题分解出的子问题的解可以合并为该问题的解。
      - 该问题所分解出的各个子问题是相互独立的，即子问题之间不包含公共的子问题。
        - 如果各子问题是不独立的，则分治法要重复地解公共的子问题，也就做了许多不必要的工作。此时虽然也可用分治法，但一般用`动态规划`较好。
  - 递归是一种编程技巧，一种解决问题的思维方式；分治算法很大程度上是基于递归的，解决更具体问题的算法思想。 

- **贪心**：每一步行动总是按某种指标选取最优的操作，只看眼前，不考虑以后可能造成的影响
  - 适用范围：最优子结构/无后效性
  - 证法：
    - 反证法：如果交换方案中任意两个元素/相邻的两个元素后，答案不会变得更好，那么可以推定目前的解已经是最优解了。
    - 归纳法：先算得出边界情况（例如 n = 1）的最优解 `F_1`，然后再证明：对于每个 n，`F_{n+1}` 都可以由 `F_{n}` 推导出结果。
  - 题型：
    - 「我们将 XXX 按照某某顺序排序，然后按某种顺序（例如从小到大）选择。」  //离线的，先处理后选择，通常适用于需要对所有选项进行全局优化的场景。
      - 示例：活动选择问题。首先对活动按结束时间排序，然后依次选择不重叠的活动。
    - 「我们每次都取 XXX 中最大/小的东西，并更新 XXX。」（有时「XXX 中最大/小的东西」可以优化，比如用优先队列维护）  //在线的，边处理边选择，适用于在数据流或实时情况下作出决策。
      - 示例：任务调度问题。在处理任务时，实时选择最优的任务进行执行。
    - 排序解法：用排序法常见的情况是输入一个包含几个（一般一到两个）权值的数组，通过排序然后遍历模拟计算的方法求出最优值。  //适用简单优化问题：如最小覆盖子集、最小化运输成本等问题。
      - 示例：假设我们需要找到能完成的活动集合，可以通过对活动按结束时间排序来解决。
    - 后悔解法：思路是无论当前的选项是否最优都接受，然后进行比较，如果选择之后不是最优了，则反悔，舍弃掉这个选项；否则，正式接受。如此往复。  //适用动态优化问题：如背包问题，可以动态地选择物品，及时调整选择。
      - 示例：在背包问题中，虽然可能第一次选择的物品不是最佳的，但通过后悔机制，我们可以在后续的选择中放弃不优的物品，调整选择，以达到最优。
    - 贪心算法与动态规划的不同在于它对每个子问题的解决方案都做出选择，不能回退。动态规划则会保存以前的运算结果，并根据以前的结果对当前进行选择，有回退功能。

- **排序**：
  - 稳定性：指相等的元素经过排序之后相对顺序是否发生了改变。
    - 基数排序、计数排序、插入排序、冒泡排序、归并排序是稳定排序。
    - 选择排序、堆排序、快速排序、希尔排序不是稳定排序。
  - 选择排序：不稳定/n^2
    - 每次找出第 i 小的元素（也就是 A_{i..n} 中最小的元素），然后将这个元素与数组第 i 个位置上的元素交换。
    ```cpp
    void selection_sort(int* a, int n) {
      for (int i = 1; i < n; ++i) {
        int ith = i;
        for (int j = i + 1; j <= n; ++j) 
          if (a[j] < a[ith]) ith = j;
      }
      swap(a[i], a[ith]);
    }
    ```
  - 冒泡排序：稳定/n^2
    - 每次检查相邻两个元素，如果前面的元素与后面的元素满足给定的排序条件，就将相邻两个元素交换。当没有相邻的元素需要交换时，排序就完成了。经过 i 次扫描后，数列的末尾 i 项必然是最大的 i 项，因此冒泡排序最多需要扫描 n-1 遍数组就能完成排序。
    ```cpp
    // 假设数组的大小是 n + 1，冒泡排序从数组下标 1 开始
    void bubble_sort(int *a, int n) {
      bool flag = true;
      while (flag) {
        flag = false;
        for (int i = 1; i < n; ++i) {
          if (a[i] > a[i + 1]) {
            flag = true;
            int t = a[i];
            a[i] = a[i + 1];
            a[i + 1] = t;
          }
        }
      }
    }
    ```
  - 插入排序：稳定/n^2
    - 将待排列元素划分为「已排序」和「未排序」两部分，每次从「未排序的」元素中选择一个插入到「已排序的」元素中的正确位置。
    ```cpp
    void insertion_sort(int arr[], int len) {
      for (int i = 1; i < len; ++i) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
          arr[j + 1] = arr[j];
          j--;
        }
        arr[j + 1] = key;
      }
    }
    ```
    - 析半插入排序：通过二分算法优化性能，在排序元素数量较多时优化的效果比较明显。
  - 计数排序：稳定/n+值域
    - 使用一个额外的数组 C，其中第 i 个元素是待排序数组 A 中值等于 i 的元素的个数，然后根据数组 C 来将 A 中的元素排到正确的位置。
      - 计算每个数出现了几次
      - 求出每个数出现次数的前缀和  //可以为重复元素确定一个唯一排名
      - 利用出现次数的前缀和，从右至左计算每个数的排名
      ```cpp
      constexpr int N = 100010; // 最大元素数量
      constexpr int W = 100010; // 值的范围上限

      int n, w, a[N], cnt[W], b[N];

      void counting_sort() {
        memset(cnt, 0, sizeof(cnt)); // 初始化计数数组 cnt
        for (int i = 1; i <= n; ++i) ++cnt[a[i]]; // 统计每个元素的出现次数
        for (int i = 1; i <= w; ++i) cnt[i] += cnt[i - 1]; // 计算前缀和，将 cnt 转换为排序后的位置
        for (int i = n; i >= 1; --i) b[cnt[a[i]]--] = a[i]; // 倒序遍历，将元素放入正确的位置
      }
      ```
  - 基数排序：稳定/n+k
    - 基数排序将待排序的元素拆分为 k 个关键字，逐一对各个关键字排序后完成对所有元素的排序。
      - 如果是从第 1 关键字到第 k 关键字顺序进行比较，则该基数排序称为 MSD 基数排序
        - 将待排序的元素拆分为 k 个关键字，先对第 1 关键字进行稳定排序，然后对于每组 具有相同关键字的元素 再对第 2 关键字进行稳定排序（`计数排序`，递归执行）……最后对于每组 具有相同关键字的元素 再对第 k 关键字进行稳定排序。
      - 如果是从第 k 关键字到第 1 关键字顺序进行比较，则该基数排序称为 LSD 基数排序。
        - 将待排序的元素拆分为 k 个关键字，然后先对 所有元素 的第 k 关键字进行稳定排序，再对 所有元素 的第 k-1 关键字进行稳定排序，再对 所有元素 的第 k-2 关键字进行稳定排序……最后对 所有元素 的第 1 关键字进行稳定排序，这样就完成了对整个待排序序列的稳定排序。
  - 快速排序：不稳定
    - 通过`分治`的方式来将一个数组排序
      - 将数列划分为两部分（要求保证相对大小关系）  //如保证前一个子数列中的数都小于后一个子数列中的数。为了保证平均时间复杂度，一般是随机选择一个数 m 来当做两个子数列的分界。
      - 递归到两个子序列中分别进行快速排序
      - 不用合并，因为此时数列已经完全有序
      ```cpp
      template <typename T>
      void quick_sort(T arr[], const int len) {
        if (len <= 0) return;
        Range r[len]; // 栈，用来存储要处理的区间
        int p = 0;
        r[p++] = Range(0, len - 1); // 初始区间
        while (p) {
          Range range = r[--p]; // 取出栈顶区间
          if (range.start >= range.end) continue;
          T mid = arr[range.end]; // 选择最右侧元素作为枢轴
          int left = range.start, right = range.end - 1;
          while (left < right) {
            while (arr[left] < mid && left < right) left++; // 从左向右找到一个大于等于 mid 的元素
            while (arr[right] >= mid && left < right) right--; // 从右向左找到一个小于 mid 的元素
            swap(arr[left], arr[right]); // 交换两者
          }
          if (arr[left] >= arr[range.end]) swap(arr[left], arr[range.end]); // 将枢轴放置到正确的位置
          else left++;
          r[p++] = Range(range.start, left - 1); // 压入左区间
          r[p++] = Range(left + 1, range.end); // 压入右区间
        }
      }
      ```
      - 朴素优化思想：
        - 通过 `三数取中`（即选取第一个、最后一个以及中间的元素中的中位数）的方法来选择两个子序列的分界元素（即比较基准）。这样可以避免极端数据（如升序序列或降序序列）带来的退化
        - 当序列较短时，使用 `插入排序` 的效率更高
        - 每趟排序后，将与分界元素相等的元素聚集在分界元素周围，这样可以避免极端数据（如序列中大部分元素都相等）带来的退化
      - 快速排序优化方式：
        - 三路快速排序：随机选取分界点 m 后，将待排数列划分为三个部分：小于 m、等于 m 以及大于 m。这样做即实现了将与分界元素相等的元素聚集在分界元素周围这一效果。
        ```cpp
        // 模板的 T 参数表示元素的类型，此类型需要定义小于（<）运算
        template <typename T>
        // arr 为需要被排序的数组，len 为数组长度
        void quick_sort(T arr[], const int len) {
          if (len <= 1) return;
          // 随机选择基准（pivot）
          const T pivot = arr[rand() % len];
          // i：当前操作的元素下标
          // arr[0, j)：存储小于 pivot 的元素
          // arr[k, len)：存储大于 pivot 的元素
          int i = 0, j = 0, k = len;
          // 完成一趟三路快排，将序列分为：
          // 小于 pivot 的元素 | 等于 pivot 的元素 | 大于 pivot 的元素
          while (i < k) {
            if (arr[i] < pivot)
              swap(arr[i++], arr[j++]);
            else if (pivot < arr[i])
              swap(arr[i], arr[--k]);
            else
              i++;
          }
          // 递归完成对于两个子序列的快速排序
          quick_sort(arr, j);
          quick_sort(arr + k, len - k);
        }
        ```
        - 内省排序：将快速排序的最大递归深度限制为 ``\lfloor \log_2n \rfloor``，超过限制时就转换为堆排序。
        - 
  - 归并排序：
  - 堆排序：
  - 桶排序：
  - 希尔排序：
  - 锦标赛排序：
  - Tim 排序：
  - 

- **前缀和&差分**：

- **二分**：

- **倍增**：

- **构造**：





















      

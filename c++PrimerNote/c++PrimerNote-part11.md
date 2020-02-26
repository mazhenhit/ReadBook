# 第十一章 关联容器操作

## 11.1 使用关联容器

map、set

## 11.2 关联容器概述

### 11.2.1 定义关联容器

map、set中的关键字必须是唯一的，但是multimup和multiset没有这个限制。

### 11.2.2 关键字类型的要求

默认情况下，标准库使用<运算符来比较两个关键字。

关键字必须是严格弱序，即：小于等于

### 11.2.3 pair类型

定义在头文件utility中

pair的数据成员是public的，通过first和second访问。

可以使用make_pair()来生成pair对象。

## 11.3 关联容器操作

### 11.3.1 关联容器迭代器

### 11.3.2 添加元素

insert()

返回值是一个pair，其中first是一个迭代器，指向具有给定关键字的元素，second是一个bool值，指出插入成功还是已经存在于容器中。

### 11.3.3 删除元素

`c.erase` 从c中删除每个关键字为k的元素。返回一个size_type值，指出删除的元素的数量。

`c.erase(p)` 从c中删除迭代器p指定的元素。p必须指向c中一个真实元素，不能等于c.end()。

`c.erase(b, e)` 删除迭代器对b和e所表示的范围中的元素。

### 11.3.4 map的下标操作

`map`和`unordered_map`容器提供了下标运算符个一个对应的at函数。

使用一个不在容器中的关键字作为下标，会添加一个具有此关键字的元素发哦map中。

```
c[k] 返回关键字为k的元素。如果k不在c中，添加一个关键字为k的元素，对其进行值初始化。
c.at(k) 访问关键字为k的元素，带参数检查；若k不在c中，抛出一个out_of_range异常。
```

### 11.3.5 访问元素

`c.find(k)` 返回一个迭代器，指向第一个关键字为k的元素，若k不在容器中，则返回尾后迭代器

`c.count(k)` 返回关键字等于k的元素的数量

如果一个`multimap`或`multiset`中有多个元素具有给定关键字，则这些元素在容器中会相邻存储

`lower_bound` 返回迭代器第一个具有给定关键字的元素

`upper_bound` 返回迭代器指向最后一个匹配给定关键字的元素之后的位置

### 11.3.6 一个单词转换的map

## 11.4 无序容器

`unorder_map` `unorder_set`

```
c.bucket_count()	正在使用的痛的数目

c.max_bucket_count()	容器能容纳的最多的桶的数量

c.bucket_size(n)	第n个桶中有多少个元素

c.bucket(k)	关键字为k的元素在哪个桶中
```

```
local_iterator	可以用来访问桶中元素的迭代器类型

const_local_iterator	容器能容纳的最多的桶的数量

c.begin(n)	c.end(n)	桶n的首元素迭代器和尾后迭代器

c.cbegin(n)	c.cend(n)	与前两个函数类似，但返回const_local_iterator
```

```
c.load_factor()	每个桶的平均元素数量，返回float值

c.max_load_factor()	c试图维护的平均桶大小，返回float值

c.refash(n)	重组存储，使得bucket_count>=n

c.reserve(n)	重组存储，使得c可以保存n的元素且不必rehash
```

不能直接定义关键字为自定义类类型的无序容器。

需要提供hash函数和相等判断函数

例如：

```
using SD_multiset = unordered_multiset<Sales_data, decltype(hasher)*, decltype(eqOp)*>;

SD_,multiset bookstore(42, hasher, eqOp); //42 为桶的数量
```


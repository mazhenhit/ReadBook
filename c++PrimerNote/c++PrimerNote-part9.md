# 第九章 顺序容器
## 9.1 顺序容器概述
顺序不依赖元素的值，而是与元素加入容器时的位置相对应的。

- vector：可变大小数组。快速随机访问。在尾部之外的位置插入或删除元素可能很慢。
- deque：双端队列。支持快速随机访问。在头尾位置插入、删除速度很快
- list：双向列表。只支持双向顺序访问。在list中任何位置进行插入、删除操作速度都很快。
- forward_list：单项链表。只支持单项顺序访问。在链表任何位置进行插入删除操作速度都很快。
- array：固定大小数组。支持快速随机访问。不能添加或删除元素。
- string：与vector相似的容器，专门用于保存字符。

## 9.2 容器库概览
### 9.2.1 迭代器
### 9.2.2 容器类型成员
### 9.2.3 begin和end成员
### 9.2.4 容器定义和初始化
标准库array具有固定大小

```cpp
array<int, 10> copy = digits;
```
### 9.2.5 赋值和swap
除array外，swap不对任何元素进行拷贝、删除或者插入操作，因此可以保证在常数时间内完成
### 9.2.6 容器大小操作
forward_list不支持size操作
### 9.2.7 关系运算符
## 9.3 顺序容器操作
### 9.3.1 向顺序容器添加元素
`array`不支持

`push_back`：讲一个元素追加到一个vector的尾部

`push_front`：将元素插入到容器头部

`insert`：将元素插入到迭代器所指定位置之前，适合list、forward_list，返回指向新元素的迭代器

`emplace`操作：emplace、emplace_front、emplace_back 构造元素放置在对应位置

### 9.3.2 访问元素
在容器中访问元素的成员函数返回的都是引用  

    auto &v = c.back()  //引用
    auto v2 = c.back()  //拷贝

### 9.3.3 删除元素

```
c.pop_back()
c.pop_front()
c.erase(p)
c.erase(p, e)
c.clear()
```

### 9.3.4 特殊的forward_list操作

```cpp
lst.before_begin()
lst.cbefore_begin()
lst.insert_after(p, t)
lst.insert_after(p, n, t)
lst.insert_after(p, b, e)
lst.insert_after(p, il)
```

```cpp
emplace_after(p, args)

lst.erase_after(p)
lst.erase_after(b, e)
```

### 9.3.5 改变容器大小
resize增大或缩小容器，不适用array

	c.resize(n)
	c.resize(n, t)

### 9.3.6 容器操作可能是迭代器失效
## 9.4 vector对象是如何增长的
管理容量的成员函数

	c.shrink_to_fit()  请将capacity()减少为与size()相同大小
	c.capacity()       不重新分配内存空间的话，c可以保存多少元素
	c.reserve(n)       分配至少能容纳n个元素的内存空间

## 9.5 额外的string操作

### 9.5.1 构造string的其他方法

	string s(cp, n)
	string s(s2, pos2)
	string s(s2, pos2, len2)


`s.substr(pos,n)` 返回一个string，包含pos开始，长度为n个字符的拷贝

    string s2 = s.substr(0, 5)

### 9.5.2 改变string的其他方法
	insert
	erase
	assign
	append
	replace
### 9.5.3 string搜索操作
```
find
rfind
find_first_of      在s中查找args中任何一个字符第一次出现的位置
find_last_of       在s中查找args中任何一个字符最后一次出现的位置
find_first_not_of  在s中查找第一个不在args中的字符
find_last_not_of   在s中查找最后一个不在args中的字符
```


可以添加pos，指定开始查找的位置

### 9.5.4 compare函数

### 9.5.5 数值转换
```cpp
to_string
stoi(s, p, b)
stol(s, p, b)
stof(s, p)
stoul(s, p)
stod(s, p)
stold(s, p)
```

## 9.6 容器适配器
本质上，一个适配器是一种机制，能使某种事物的行为看起来像另外一种不同的类型。  
三种：`stack、queue、priority_queue`  

默认情况下，stack和queue是基于deque实现的，priority_queue是在vector之上实现的。  

栈适配器：  
默认基于deque实现，也可以在list或vector上实现。

	s.pop()          删除栈顶元素，但是不返回该元素
	s.push(item)     创建一个新元素压入栈顶
	s.emplace(args)  由args构造
	s.top()          返回栈顶元素，但不将元素弹出栈

队列适配器：

```
queue 默认基于deque实现，也可以用list或vector实现
priority_queue 默认基于vector实现，也可以用deque实现
q.pop()    删除queue的首元素或priority_queue的最高优先级的元素，但不返回此元素
q.front()  返回首元素或尾元素，但不删除此元素
q.back()   只适用于queue
q.top()    返回最高优先级元素，但不删除该元素，只适用priority_queue
```




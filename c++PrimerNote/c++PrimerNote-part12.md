# 第十二章 动态内存

## 12.1 动态内存与智能指针

### 12.1.1 shared_ptr类

适用于`shared_ptr`和`unique_ptr`都支持的操作：

```cpp
shared_ptr<T> sp     空智能指针，可以指向类型为T的对象

unique_ptr<T> up

p				将p用作一个条件判断，若p指向一个对象，则为true

*p				解引用p，获得它指向的对象

p->mem			等价于(*p)->mem

p.get()			返回p中保存的指针。要小心使用，若智能指针释放了其对象，返回的指针所指向的对象也就消失了

swap(p, q)		交换p和q中的指针

p.swap(q)
```

shared_ptr独有操作：

```cpp
make_shared<T>(args)	返回一个shared_ptr，指向一个动态分配的类型为T的对象。使用args初始化此对象

shared_ptr<T>p(q)		p是shared_ptr q的拷贝；此操作会递增q中的计数器。q中的指针必须能转换为T*

p=q					   p和q都是shared_ptr，所保存的指针必须能相互转换。
                        此操作会递减p的引用计数，递增q的引用计数；
                        若p的引用计数变为0，则其管理的原内存释放

p.unique()			   若p.use_count()为1，返回true；否则返回false

p.use_count()           返回与p共享对象的只能指针数量；可能很慢，主要用于调试
```



### 12.1.2 直接内存管理

### 12.1.3 shared_ptr和new结合使用

接受指针参数的智能指针构造函数是explicit的，因此不能讲内置指针隐式转换为一个智能指针。

### 12.1.4 智能指针和异常

使用我们自己的释放操作：

shared_ptr<connection> p(&c, end_connection)

## 12.2 动态数组



## 12.3 使用标准库：文本查询程序



### 12.3.1 文本查询程序设计

### 12.3.2 文本查询程序类的定义
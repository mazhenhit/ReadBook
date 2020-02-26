# 第六章 函数

## 6.1 函数基础

### 6.1.1 局部对象

局部静态对象：程序的执行路径第一次经过对象定义语句时初始化，并且直到程序终止才被销毁，在此期间即使对象所在的函数结束执行也不会对它有影响。

### 6.1.2 函数声明

含有函数声明的头文件应该被包含到定义函数的源文件中。

### 6.1.3 分离式编译

## 6.2 参数传递

### 6.2.1 传值参数

### 6.2.2 传引用参数

使用引用避免拷贝

使用引用形参返回额外信息 

### 6.2.3 const形参和实参

当形参有顶层const时，传给它常量对象或者非常量对象都是可以的。

尽量使用常量引用。

把函数不会改变的形参定义为普通的引用是一种比较常见的**错误**。

### 6.2.4 数组形参

使用标准库规范：  const int *beg，const int *end

显示传递一个表示数组大小的形参

### 6.2.5 main：处理命令行选项

int argc, char **argv

当使用argv中的实参时，argv[0]保存程序的名称，而非用户输入

### 6.2.6 含有可变形参的函数

1、如果函数的实参数量未知，但是类型相同，使用initializer_list类型的形参。

```cpp
void error_msg(initializer_list<string> il)
```

2、省略形参

​       大多数类类型的对象在传递给省略符形参时都无法正确拷贝

## 6.3 返回类型和return语句

### 6.3.1 无返回值函数

### 6.3.2 有返回值函数

不要返回局部对象的引用或指针

### 6.3.3 返回数组指针

## 6.4 函数重载

如果同一作用域内的几个函数名字相同但形参列表不同，我们称之为重载。

### 6.4.1 重载与作用域

## 6.5 特殊用于语言特性

### 6.5.1 默认实参

### 6.5.2 内联函数和constexpr函数

### 6.5.3 调试帮助

## 6.6 函数匹配

### 6.6.1 调试帮助

## 6.7 函数指针



# 第七章 类
## 7.1 定义抽象数据类型
### 7.1.1 设计Sales_data
### 7.1.2 定义改进的额Sale_data类
定义在类内部的函数式隐式的inline函数  

紧随参数列表之后的const关键字：修改隐式this指针的类型

默认情况下，this的类型是指向类类型非常量版本的常量指针 

C++语言的做法：允许把const关键字放在成员函数的参数列表之后，表示this是一个指向常量的指针。

这种函数称作：常量成员函数

### 7.1.3 定义类相关的非成员函数
### 7.1.4 构造函数
`=default` 默认构造函数，用来要求编译器成成构造函数

### 7.1.5 拷贝、赋值和析构

## 7.2 访问控制与封装
clas和struct唯一的区别就是默认的访问权限  

### 7.2.1 友元
类可以允许其他类或者函数访问他的非公有成员，方法是令其他类或函数成为他的友元  
添加一条以friend关键字开始的函数声明语句即可

## 7.3 类的其他特性
### 7.3.1 类成员再探
### 7.3.2 返回*this成员函数
一条语句进行一连串操作
### 7.3.3 类类型
### 7.3.4 友元再探
每个类负责控制自己的友元类或友元函数
## 7.4 类的作用域
### 7.4.1 名字查找与类的作用域
## 7.5 构造函数再探
### 7.5.1 构造函数初始值列表
如果成员是const、引用，或者属于某种未提供默认构造函数的类类型，我们必须通过构造函数初始值列表为这些成员提供初值。
### 7.5.2 委托构造函数
委托构造函数使用其他构造函数执行初始化过程
### 7.5.3 默认构造函数的作用
### 7.5.4 隐式的类类型转换
构造函数声明为`explicit` 抑制构造函数定义的隐式转换  
### 7.5.5 聚合类
### 7.5.6 字面值常量类
## 7.6 类的静态成员
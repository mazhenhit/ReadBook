# 第三章 字符串、向量、数组 #
## 3.1 命名空间的using声明 ##
```cpp
using namespce std;
```

## 3.2 标准库类型string ##

```cpp
#include <string>
using std::string
```

### 3.2.1 初始化
```cpp
string s3("value");
string s3 = "value";
string s4(10, 'c');
```

### 3.2.2 string对象上的操作
```cpp
s.empty()
s.size()
s[n]
s1+s2
s1==s2
```

string::size_type类型是s.size()返回的数据类型

string s6 = s1 + "Hello," + "world";  

字面值与string类型相加，必须确保每个加号的两侧运算对象有一个是string

### 3.2.3 处理string对象中的字符
```cpp
for(auto c : str)
	cout << c << endl;

decltype(s.size()) punct_cnt = 0;
```

## 3.3 标准库类型vector
vector是模板热不是类型

由vector生成的类型必须包含vector  

### 3.3.1 定义和初始化vector对象

```cpp
vector<T> v2(v1)
vector<T> v2=v1  等价上一种声明
vector<T> v3(n, val)
vector<T> v4(n)
vector<T> v5{a, b, c, d}
vector<T> v5={a, b, c, d} 等价上一种声明
```

### 3.3.2 向vector中添加元素

```cpp
push_back()
```

先定义一个空的vector，再插入元素，性能更好  

### 3.3.3 其他vector操作

大多与string相关操作类似  

```cpp
v.empty()
v.size()  
v1==v2  
<  
<=  
```

## 3.4 迭代器介绍 ##

### 3.4.1 使用迭代器

	auto b = v.begin(), e = v.end();
b：v的第一个元素  
e：v尾元素的下一个位置  

### 3.4.2 迭代器运算

```cpp
iter + n
iter - n
iter += n
iter1 - iter2
>,>=,<,<=
```

## 3.5 数组 ##

### 3.5.1 定义和初始化内置数组
a[b] b为常量或常量表达式

不存在引用的数组

### 3.5.2 访问数组元素

### 3.5.3 指针与数组

```cpp
begin(array)
end(array)
```

内置下标不是无符号类型

### 3.5.4 C风格字符串

`string`更安全、高效

### 3.5.5 与旧代码的接口

```cpp
char *str = s.c_str();int int_arr[] = {0, 1, 2, 3, 4};

vector<int> ivec(begin(int_arr), end(int_arr));

vector<int> ivec(int_arr + 1, int_arr + 4);
```

## 3.6 多维数组 ##
多维数组其实是数组的数组

```cpp
for(auto &row : ia)
```

多维数组需要引用，防止数组被自动转换为指针


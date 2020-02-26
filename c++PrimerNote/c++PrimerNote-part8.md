# 第八章 IO库
## 8.1 IO类
头文件：

```cpp
iostream
fstream
sstream
```

### 8.1.1 IO对象无拷贝或赋值
不能拷贝或对IO对象赋值
### 8.1.2 条件状态
```cpp
strm::iostate 提供了表达条件状态的完整功能  
strm::badbit  指出流已崩溃  
strm::failbit 用来支出一个IO操作失败了  
strm::eofbot  用来支出流到达了文件结束  
strm::goodbit 用来支出流未处于错误状态，值为0  

s.eof() 
s.fail()
s.bad()
s.good()
s.clear()
s.clear(flags)
s.setstate(flags)
s.rdstate()       返回当前条件状态，返回值为iostate
```


### 8.1.3 管理输出缓冲
刷新缓冲区：  

```cpp
endl  
ends  
flush  
```

unitbuf操作符：每次写操作之后都flush操作。

```cpp
cout << unitbuf;
cout << nounitbuf; //取消
```

关联输入输出流：

`x.tie(&o)` 将流x关联到输出流

## 8.2 文件输入输出

### 8.2.1 使用文件流对象

`ifstream in(file);` 构造一个ifstream并打开给定文件

当一个fstream对象被销毁时，close会自动被调用  

### 8.2.2 文件模式
```cpp
in：读方式打开
out: 写方式打开
app：每次写操作均定位到文件末尾
ate：打开文件后立刻定位到文件末尾
trunc：截断文件
binary：二进制方式  
```

## 8.3 string流

    istringstream
    ostringstream
    stringstream

`strm.str()` 返回strm所保存的string的拷贝
`strm.str(s)` 将string s拷贝到strm中，返回void

### 8.3.1 使用istringstream

    string line, word;
    vector<PersonInfo> people;
    while (getline(cin, line))
    {
        PersonInfo info;
        istringstream record(info);
        record << info.name;
        while (record >> word)
        info.phones.push_back(info);
        people.push_back(info);
    }

### 8.3.2 使用ostringstream


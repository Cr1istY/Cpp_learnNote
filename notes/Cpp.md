# C++入门教程

## 一、导学，关于C++

### 面向过程和面向对象

c语言最大的缺陷，就是在于他面向过程的思维，在如今看来不够高效。

因此，面向对象的cpp语言应运而生。

#### 面向过程（POP）

- 以过程（procedure）为中心的编程范式
- 按照计算机执行命令的顺序，从上到下顺序设计程序

#### 面向对象（OOP）

- 以对象（object）为核心的编程范式
- 对象是类（class）的实例，类中包括了数据的定义和对数据的操作方法

### C++的特点

- 贴近底层、运行速度快
- 编译型语言
- 静态类型语言
- 结构化教学语言
- 面向对象语言
- 面向泛式编程语言
- 功能强大，也复杂、难以掌握

### C++的应用领域

- 桌面应用
- 系统开发
- 底层架构
- 游戏开发
- **嵌入式开发**

### C++代码运行和标准

#### 编译型语言

将整个源代码编译成机器码，再运行机器码

例如：C++、C

#### 解释型语言

由解释器将代码逐行翻译成机器码，逐行运行

例如：Python、JavaScript

#### C++运行

1. 将源代码编译成可目标代码
1. 目标代码与库文件链接，生成可执行文件
1. 运行可执行文件

#### C++标准

- C++98
- C++03
- C++11
- C++14
- C++17
- C++20

## 二、正式开始

### 1.第一个C++程序

```cpp
#include <iostream>

int main() {
	std::cout << "Hello, World!" << std::endl;
	return 0;
}
```

- std 命名空间
- :: 作用域运算符

### 2.变量和数据类型

#### 变量的声明和赋值
```cpp
// 数据类型 变量名 = 初始值;
int a = 10;
```

#### 标识符

由字母、数字、下划线组成，不能以数字开头

不能使用关键字命名

常使用驼峰命名法命名

#### 常量

- 使用`#define`定义常量，不推荐
- 使用`const + 数据类型`定义常量

#### 整形

| 类型 | 描述 | 字节数 | 范围 |
| --- | --- | --- | --- |
| int | 整数 | 4 | -2147483648 ~ 2147483647 |
| short | 短整数 | 2 | -32768 ~ 32767 |
| long | 长整数 | 4 | -2147483648 ~ 2147483647 |
| long long | 长长整数 | 8 | -9223372036854775808 ~ 9223372036854775807 |
| unsigned int | 无符号整数 | 4 | 0 ~ 4294967295 |
|char|字符|1|-128 ~ 127|
|bool|布尔|1|true/false|

使用原则：

1. int不够用，直接使用long long
1. 不能为负直接使用unsigned

#### 浮点型

| 类型 | 描述 | 字节数 | 范围 |
| --- | --- | --- | --- |
| float | 单精度浮点数 | 4 | 3.4e-38 ~ 3.4e38 |
| double | 双精度浮点数 | 8 | 1.7e-308 ~ 1.7e308 |

还可以使用科学计数法表示

5.2e2 = 5.2 * 10^2 = 520

### 3.运算符

#### 优先级

乘除运算大于加减运算，平级从左往右依次计算，括号优先级最高

#### 算术运算符

|运算符|功能|
|---|---|
|+|加法、表示正数|
|-|减法、表示负数|
|*|乘法|
|/|除法|
|%|求余、取模|

#### 赋值运算符

用“=”号表示赋值

左值必须是可以修改的变量，右值可以是常量、变量、表达式

同时，在c++中，可以使用{}进行初始化赋值
```cpp
int a = {10};
int a = 10;
```
两者等效

#### 复合赋值运算符

```cpp
sum+= 10;
sum/= 10;
```
本质上都是二合一，即将运算符和赋值运算符合并

同时，还有`++a` `--b`等常见操作

值得注意的是：

`++a`前置时，先运算再进行返回

`a++`后置式，先返回再运算

#### 关系运算符

|运算符|功能|
|---|---|
|==|等于|
|!=|不等于|
|>|大于|
|<|小于|
|>=|大于等于|
|<=|小于等于|

#### 逻辑运算符

|运算符|功能|
|---|---|
|&&|与|
|\|\||或|
|!|非|

#### 条件运算符
```cpp
int a = 10;
int b = 20;
int max = a > b ? a : b;
```
等效于
```cpp
int max;
if (a > b) {
	max = a;
} else {
	max = b;
}
```

即 ，`?`前为判断条件，`:`前为条件为真时返回值，`:`后为条件为假时返回值

#### 位运算符

位运算符操作的是每一位（bit）上的数据

|运算符|功能|
|---|---|
|&|按位与|
|\||按位或|
|^|按位异或|
|~|按位取反|
|<<|左移|
|>>|右移|

#### 类型转换

- 隐式类型转换
> - 将长度较小的数据类型转换为长度较大的数据类型
> - 这样可以避免精度丢失

- 显式类型转换（强制类型转换）
```cpp
int a = 10;
double b = (double)a;
double c = double(a);
static_cast<double>(a);
```

(数据类型)变量 | 数据类型(变量) | 使用c++内置强制类型转换函数

### 4.流程控制语句

#### 顺序结构

程序按照代码的先后顺序执行

#### 分支结构

##### if

1. if单分支

```cpp
if (条件) {
	// 代码块
}
```

2. if双分支(也可使用条件运算符)

```cpp
if(条件) {
	// 代码块
} else {
	// 代码块
}
```

3. if多分支
```cpp
if (条件1) {
	// 代码块
} else if (条件2) {
	// 代码块
} else {
	// 代码块
}
```

##### switch
```cpp
switch (表达式) {
	case 常量1:
		// 代码块
		break;
	case 常量2:
		// 代码块
		break;
	default:
		// 代码块
}
```

用于多分支判断，`break`用于跳出`switch`语句

#### 循环（迭代）结构

##### while
```cpp
while (条件) {
	// 代码块
}
```

##### do while
```cpp
do {
	// 代码块
} while (条件);
```

先执行一次循环体，再判断条件

##### for
```cpp
for (初始化; 条件; 更新) {
	// 代码块
}
```

#### 跳转

##### break
跳出循环

##### continue
跳过本次循环

##### goto和return
跳转到指定位置
```cpp
goto label;
label:
```

goto一般不使用，会导致程序逻辑混乱

return终止函数运行，并返回值


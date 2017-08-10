#### 一、基本类型
关键词| 类型|占位
|---|---|---|--|--|
bool | 布尔型|--
char|字符型|8bit
wchar_t|宽字符型|16bit
short|短整型|16bit
int|整型|16bit
long|长整型|32bit
float|单精度浮点型|6位有效数字
double|双精度浮点型|10位有效数字
long double|扩展精度浮点型|10为有效数字

#### 二、转义字符

符号 | 意义
---|---
\n|换行符 
\v| 纵向制表符
\r|回车符
\a|报警（响铃符）符
\？|疑问号
\"|双引号
\t|水平指标符
\b|退格符
\f|进纸符
\\\|反斜杠
\'|单引号
\o|空字符
==注：可以通过\ooo三个八进制数的ascii码表示特殊字符==

#### 三、初始化
1、直接初始化：列：
```
int a(1);
```
2、间接初始化：列：
```
int a=1;

```
3、区别：以后补上

4、规则：
- 基本类型：函数体外定义的变量自动初始化为0
- 类类型：不提供初始化式时通过默认构造函数初始化变量，提供初始化式时通过对应构造函数初始化变量。

#### 四、作用域

```
#include<iostream>
int global;  //全局变量，整个文件都有效
int main()
{
  int local;局部变量
  for(int i=0;i<2;i++)
  {
      int j;//代码块局部变量，该代码块有效
  }
    return 0;
}
```
#### 五、const限定符
意义：常量,

注意：
- 定义时必须初始化
- 默认为文件内的局部变量，不能被其他文件引用，如想被其他文件使用，可以指定为extern类型
- const引用为只读

#### 六、 typedef
- 作用：定义新类型
- 好处：隐藏特定类型定义；简化复杂类型定义；明确类型使用的目的

#### 七、枚举
- 枚举使用enum定义，成员值为常量
- 每个枚举都定义了一种唯一的类型
#### 八、类类型
以后完善

### 九、struct
- 可以定义类类型，成员默认为public
- 可以当c语言的结构体使用

### 十、头文件
- 避免多重包含：
```
#ifndef ***_H
#define ***_H
//头文件代码
#endif
```

#### 十、标准库
1. 命名空间
- 创建命名空间
  
```
namespace name
{
   //属于命名空间的内容，命令空间同样存在作用域
   void test()
   {
       
   }
}
```
- 使用命名空间

```
//方式一
using namespace name;
如：using namespace std;
//方式er
using name::child;
如：
using std::count;
```

2. 标准库string类型
- 初始化：

方式 | 含义
---|---
string s | 默认构造函数，为空字符串
string s(s1) | 将s初始化为s1的一个副本
string s("value")| 将s初始化为字面值的副本
string s(n,'c') |将s初始化为字符C的n个副本

- 读写

a、开头结尾遇到空白字符终止

b、使用getline（）函数读取行时会抛弃换行符，需要自行处理

- 常用操作

操作| 意义
---|---
s.empty | 判断是否为空
s.size() | 获取字符个数，为size_type类型，而不是int类型
s[n]|返回字符中，位置为n的字符，从0
开始计数
+|连接两个字符串
=|给字符串赋值，为右值的副本
==|比较两个字符串的内容
>=、>、<、<=|遵循数学的定义


3. 标准库vector类型
- 初始化

方式|意义
---|---
vector<T> v | vector 保存类型为T的对象，默认构造函数v为空
vector<T> v(v1) | v是v1的一个副本
vector<T> v(n,t)|v包含n个值为t的元素
vector<T> v(n)|v含有默认值元素的n个副本
- 常用操作

操作 |意义
---|---
v.empty() | 判断v是否为空
v.size() | 返回v中元素的个数，其类型为vector<T>::size_type
v.push_back(t)|在v末尾增加元素t
v[n]|取位置为n的元素
=|赋值
==|比较是否相等
=>、>、<=、<|与数学意义一样

- 迭代器
类型：普通迭代器和const迭代器(只读)
a、获取：
```
vector<T>::iterator iter;//普通迭代器
vector<T>::const_iterator c_iter;//const迭代器
```
b、常用操作

操作 | 意义
---|---
iter.begin() | 指向迭代器头
iter.end() | 指向迭代器末端
++、--、iter+n、iter-n|算术操作
*|解引用


#### 十、数组
1、定义和初始化
- 数组的长度（维数）必须使用已初始化的常量int、枚举、字面值常量
-显示初始化维数可有可无
-数组不允许直接赋值和复制
-数组长度的类型为size_t，而不是整型

```
const int a=2;
const int b ;
int arr[a];//ok
int arr1[b]//error
int arr2[]={1,1,1}//ok
int arr3[a]={1,1}//ok
```

#### 十一、指针
指针用于指向对象，保存的是指向对象的地址

1、 声明：

```
//风格一
vector<int> *pvec;
//风格二
int* ip1;
int* pi1，pi3;//pi1是指针，pi3是int
int a;
int pi2=&a;
```
2、 赋值

a、约束
- 0值
- 匹配类型的对象地址
- 另一对象的下一个地址
- 同类型的另一个有效指针

==注：void *指针可以保存任何类型的对象地址==

3、操作

操作| 意义
---|---
* |声明符号/解引用
++/-- |自增/自减
p+n|移动n的为值
==使用指针操作时注意边界==

4、const限定符
- 指向const对象：只读，且强迫指针也是const
```
const int a=9;
const int *pi=&a;//ok
int *pi1=&a;//error

```
- const指针:const一旦赋值则不能修改

```
int a=0;
int b;
int *const c_pi = &a ;
c_pi=&b;//error
```
- 指向const的const指针：既不能改变指针值，也不能改变所指向的值，只读，当常量使用

```
const int a=9;
const int *const c_int=*a;//
```
- 与typedef结合

```
typedfe int *pint;
 const pint pint_a;//等价于 int *const pint_a;指向int的const指针 
 
```

5、c风格的字符串：

```
char c1[]={'a','b'}//no
char c2[]={'a','b','\0'}//yes
const char *c_c3="sdfdf"//yes 
```
- 标准库：cstring

操作 |意义
---|---
strlen(s)|返回s的长度，不包括null
strcmp(s1,s2)|比较两个字符是否相同：0：相同，1：大于，2：小于
strcat(s1,s2)|将s2连接到s1
strcpy(s1,s2)|将s2复制个s1
strcat(s1,s2,n)|将s2的前n个字符连接到s1
strcpy(s1,s2n)|将s2的前n个字符复制个s1

6、动态数组
- 定义：

```
int *pia=new int[n];
const int *c_pia=new int[10]();//const对象的动态数组需要提供默认构造函数
```
==动态数组使用后需要使用delete [] type(类型)进行内存释放，防止内存泄漏==

五、表达式
1、操作符
- 仅列出不熟悉的

操作符| 意义
---|---
->| 用于指向类类型的指针调用方法或者属性
row 2 col 1 | row 2 col 2
sizeof|有三中形式：1、sizeof(type) ; 2、sizeof(exper);3、sizeof exper;用于获得表达式类型的长度，当用于指针是获得该指针占用的内存空间的大小
new|新建对象
delete|释放对象
delete|释放数组 

2、类型强制转换

转换类型|意义
---|---
dynamic_cast | 动态转换，用于运行时对象的强制转换
const_cast | 为表达式添加const性质
static_cast|静态转换
reinterport_cast|为位模式提供重新解析
(type) expr|就是强制转换

六、语句


## 七、函数
 1、返回类型
-  函数不能返回内置数组类型和和另一个函数，但可以返回一个数组指针


2、参数传递

a、非引用参数：传递副本，副本修改不影响参数
- 基本类型形参：传递副本
- 指针形参：传递地址，函数中可以修改形参的值，（改变指针的指向无效，改变指针指向的值有效）
- const形参：只对引用形参生效，非引用形参编译器会忽略
- 
b、引用类型形参：函数内修改参数会影响形参

- 普通引用实参：可修改且会受到影响
- const引用实参：不可修改，可以const引用避免复制，提高程序性能
- 指向指针的引用：如：int  *&p，从右到左理解，意味指向int类型指针的引用

c、容器类参数：通过迭代器传递，避免复制产生

d、数组类型参数传递：
- 非引用形参会忽略数组长度，并且自动转化为指向数组第一个元素的指针，注意数组越界的产生
- 应用形参会检测数组长度，不会自动转换为指针








  
 


















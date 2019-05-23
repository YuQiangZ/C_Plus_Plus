# C++学习中遇到的一些小问题

## `#include <cstdlib>`

#### **C标准通用实用库**

此标头定义了几个通用功能，包括动态内存管理，随机数生成，与环境的通信，整数算术，搜索，排序和转换。

## `#include <ctime>`

定义了两个宏，声明了四种类型和几个操作时间的函数。很多函数处理都表示当前日期（公历）和时间。有些函数处理本地时间（某个特定时区的时间）和夏令时（是确定本地时间算法的临时替代）。

```c++
srand(time(0));//先设置种子
rand();//然后产生随机数
```

> Srand是种下随机种子数，你每回种下的种子不一样，用Rand得到的随机数就不一样。为了每回种下一个不一样的种子，所以就选用Time(0)，Time(0)是得到当前时时间值（因为每时每刻时间是不一样的了）。
>
> srand(time(0)) ;
>
> 
>
> 就是给这个算法一个启动种子，也就是算法的随机种子数，有这个数以后才可以产生随机数, 
> 用1970.1.1至今的秒数，初始化随机数种子。

## C++中的强制转换函数

- static_cast
- dynamic_cast
- reinterpret_cast
- const_cast

1. static_cast 

   >   用法：static_cast < type-id > ( expression )     
   > 该运算符把expression转换为type-id类型，但没有运行时类型检查来保证转换的安全性。它主要有如下几种用法：
   > ①用于类层次结构中基类和子类之间指针或引用的转换。
   > 进行上行转换（把子类的指针或引用转换成基类表示）是安全的；
   > 进行下行转换（把基类指针或引用转换成子类表示）时，由于没有动态类型检查，所以是不安全的。
   > ②用于基本数据类型之间的转换，如把int转换成char，把int转换成enum。这种转换的安全性也要开发人员来保证。
   > ③把空指针转换成目标类型的空指针。
   > ④把任何类型的表达式转换成void类型。
   >
   > 注意：static_cast不能转换掉expression的const、volitale、或者__unaligned属性。   

2. dynamic_cast

   >   用法：dynamic_cast < type-id > ( expression )
   > 该运算符把expression转换成type-id类型的对象。Type-id必须是类的指针、类的引用或者void *；
   > 如果type-id是类指针类型，那么expression也必须是一个指针，如果type-id是一个引用，那么expression也必须是一个引用。
   >
   > dynamic_cast主要用于类层次间的上行转换和下行转换，还可以用于类之间的交叉转换。
   > 在类层次间进行上行转换时，dynamic_cast和static_cast的效果是一样的；
   > 在进行下行转换时，dynamic_cast具有类型检查的功能(如果进行下行转换,结果为0,即空指针.P664)，比static_cast更安全。  

3. reinterpret_cast

   >   用法：reinpreter_cast<type-id> (expression)
   > type-id必须是一个指针、引用、算术类型、函数指针或者成员指针。
   > 它可以把一个指针转换成一个整数，也可以把一个整数转换成一个指针（先把一个指针转换成一个整数，
   > 再?把该整数转换成原类型的指针，还可以得到原先的指针值）。
   >
   > 该运算符的用法比较多。  
   >
   > *这个没用过*

4. const_cast

   > 用法：const_cast<type_id> (expression)
   > 该运算符用来修改类型的const或volatile属性。除了const 或volatile修饰之外， type_id和expression的类型是一样的。
   > 常量指针被转化成非常量指针，并且仍然指向原来的对象；
   > 常量引用被转换成非常量引用，并且仍然指向原来的对象；常量对象被转换成非常量对象。
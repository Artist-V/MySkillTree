## C++基础

1. extern "C"
2. 断言 assert

***

## extern "C"
>Q:在C++程序中调用被C编译器遍以后的函数，为什么要加“extern C”
>A:C++语言支持函数重载，C语言不支持函数重载。函数被C++编译后在库中的名字与c语言的不同。

* 是C与C++混用头文件地经典做法
  * extern "C"，可以使链接器可靠地对两种类型地目标文件进行链接，可以抑制C++对函数名、变量名等符号进行名称重整.

***

## 断言
断言是一种编程常用手段
* 头文件<cassert> <assert.h>头文件
  * assert宏，用于在运行时进行断言
* 断言是将一个返回值总是需要`为真的判别式`放在语句中，用于排除在设计的逻辑上不应该产生的情况
  * 比如一个函数总需要输入在一定的范围内的参数，那么程序员就可以对该参数使用断言，以迫使在该参数发生异常的时候程序退出，从而避免程序陷入逻辑的混乱
* 定义NDEBUG宏来禁用assert宏
  * 通过定义NDEBUG宏可以尽量避免程序退出的状况，当程序有问题时，通过没有定义宏NDEBUG的版本，程序员则可以比较容易地找出问题的位置
  * 一旦定义了NDEBUG宏，assert宏将被展开为一条无意义的C语句，被编译器优化掉

```
  //#define  NDEBUG
  #include <cassert>
  #include <iostream>
  using namespace std;

  char* ArrayAlloc(int n)
  {
  	assert(n > 0); //断言,n必须大于0
  	return new char[n];
  }

  int main()
  {
  	char* a = ArrayAlloc(0);

  	return 0;
  }
```
* #error 预处理指令
  * #if和#error 配合：可以在预处理阶段进行断言
  * 通过预处理时的断言，用以避免一些头文件的引用问题

* 静态断言与static_assert
 go

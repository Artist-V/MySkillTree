### lambda表达式
[capture](parameters)->return-type {body}  

* lambda表达式适用于`创建匿名函数`的编译器内部会生成一个仿函数，并从其父作用域中取得参数传递给lambda函数
  * 当创建lambda函数的时候，
* 作用：
  * 可以定义匿名函数
  * 编译器会把它转成函数对象
  * “闭包”限制了外部访问，更加私有

>标准C++库中有常用算法的库<algorithm>，提供了很多算法函数，比如sort()和find()，这些函数通常需要提供`仿函数`（满足的条件之类的）。这样的仿函数，使用临时的匿名函数，既可以减少函数的数量，又会让代码变得清晰易读。

* 在qt中要使用C++11新特性，要在pro文件中加入`CONFIG += C++11`
>在qt中可以在连接信号与槽的connect函数中，用lambda表达式实现槽函数

* lambda引入符：引入lambda表达式的前导符，一对方括号
  * lambda表达式可以使用与其相同范围内的变量
  * 作用：表明该lambda表达式以何种方式`捕获`（变量在lambda表达式中被捕获，构成了一个闭包）

（1）[ ] : 不捕获任何外部变量
（2）[=] : 以值形式捕获所有外部变量
（3）[&] : 以引用形式捕获所有外部变量
（4）[x, &y] : x以传值形式捕获，y以引用形式捕获
（5）[=, &z] : z以引用形式捕获，其余变量以传值形式捕获
（6）[&, x]  : x以值形式捕获，其余变量以引用形式捕获  
  * [=] 和 [&]形式，lambda表达式可以直接使用this指针
  * []的形式要使用this指针必须显示传入（因为它没有捕获任何外部变量）
  * 传值和传引用的区别：
    * 传值的形式：lambda体不允许修改外部变量，`会引发编译错误`
    * 传引用的形式：lambda体允许修改外部变量

```
例子：
  void abssort(float *x,unsigned N)
  {
    std::sort(x, x + N, [](float a,float b)
                        {
                          return (std::abs(a) < std::abs(b));
                        })
  }
```
[参考文章](https://blog.csdn.net/caogenwangbaoqiang/article/details/79438279)

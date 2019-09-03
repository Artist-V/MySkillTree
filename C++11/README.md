## c++11的新特性

| INDEX1 | INDEX2 |
| :----: | :----: |
| 智能指针 | lambda表达式

1. nullptr
2. lambda表达式



***
### nullptr
1. nullptr
* 一个新的C++关键字，代表`空指针常量`
* 用来代替高风险的NULL宏和0字面量
* nullptr是强类型的，所有和指针有关的都可以用nullptr，包括函数指针和成员指针
```
  void fun(int);
  void fun(int *);
  ...
  f(0) ;  // 调用fun(int);
  f(nullptr);   // 调用fun(int *);
```

***

###

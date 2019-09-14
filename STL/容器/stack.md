## stack
* stack是堆栈容器，是一种“先进后出”的容器。
* stack是简单地装饰deque容器而成为另外的一种容器。

#### stack默认构造
```
stack <T> stkT;  
stack <int> stkInt;            //一个存放int的stack容器。
stack <float> stkFloat;        //一个存放float的stack容器。
stack <string> stkString;      //一个存放string的stack容器
```

#### stack插入删除
```
stack.push(int num);   //往栈头添加元素
stack.pop();           //从栈头移除第一个元素
```

#### stack拷贝构造与赋值
```
stack(const stack &stk);		         //拷贝构造函数
stack& operator=(const stack &stk);	 //重载等号操作符
```


#### 数据存取
```
const int &top() const;	  //返回最后栈顶元素
int &top();               //返回最后栈顶元素
```


#### stack的大小
```
stack.empty();       //判断堆栈是否为空
stack.size(); 	     //返回堆栈的大小
```

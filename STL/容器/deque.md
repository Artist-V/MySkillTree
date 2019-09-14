## deque
* deque是“double-ended queue”，双端数组
* 可以随机存取元素（支持索引值直接存取， 用operator[]或at()）
* deque头部和尾部添加或移除元素都非常快速。但是在中部安插元素或移除元素比较费时。

#### deque默认构造
```
deque <int> deqInt;         //一个存放int的deque容器
deque <float> deqFloat;     //一个存放float的deque容器
deque <string> deqString;   //一个存放string的deque容器
deque <CA> deqCA;           //一个存放自定义类型CA的deque容器
```

#### deque带参数构造
```
deque(beg,end);            //构造函数将[beg, end)区间中的元素拷贝给本身。注意该区间是左闭右开的区间。
deque(n,elem);             //构造函数将n个elem拷贝给本身。
deque(const deque  &deq);  //拷贝构造函数。
```


#### deque头插尾插，头删尾删
```
deque.push_back(int num);	  //在容器尾部添加一个数据
deque.push_front(int num);	//在容器头部插入一个数据
deque.pop_back();    		//删除容器最后一个数据
deque.pop_front();		  //删除容器第一个数据
```

#### deque数据存取
```
deque.at(int index);  //返回索引idx所指的数据，如果idx越界，抛出out_of_range
deque[int index];     //返回索引idx所指的数据，如果idx越界，不抛出异常，直接出错
deque.front();        //返回第一个数据
deque.back();         //返回最后一个数据
```

#### deque与迭代器
```
deque.begin();   //返回容器中第一个元素的迭代器
deque.end();     //返回容器中最后一个元素之后的迭代器
deque.rbegin();  //返回容器中倒数第一个元素的迭代器
deque.rend();    //返回容器中倒数最后一个元素之后的迭代器
```

#### deque赋值
```
deque.assign(beg,end);    //将[beg, end)区间中的数据拷贝赋值给本身。注意该区间是左闭右开的区间。
deque.assign(n,elem);  //将n个elem拷贝赋值给本身。
deque& operator=(const deque &deq);	//重载等号操作符
deque.swap(deq);  // 将vec与本身的元素互换
```


#### deque的大小
```
deque.size();	        //返回容器中元素的个数
deque.empty();	      //判断容器是否为空
deque.resize(num);    //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除。
deque.resize(num, elem);  //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除。
```


#### deque的删除
```
deque.clear();	//移除容器的所有数据
deque.erase(beg,end);  //删除[beg,end)区间的数据，返回下一个数据的位置。
deque.erase(pos);    //删除pos位置的数据，返回下一个数据的位置。
```

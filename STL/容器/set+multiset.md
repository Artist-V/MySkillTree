## set / multiset
* set是一个集合容器，其中所包含的元素是唯一的，集合中的元素按一定的顺序排列。元素插入过程是按排序规则插入，所以不能指定插入位置。
* set采用`红黑树`变体的数据结构实现，红黑树属于平衡二叉树，在插入和删除操作上比vector快
* set不可以直接存取元素（不可使用at()和operator[])
* multiset和set的区别：
  * set支持键值唯一，每个元素值只能出现一次
  * multiset中同一值可以出现多次
* 不可以直接修改set或multiset容器中的元素值，因为该类容器是自动排序的
  * 如果希望修改一个元素值，必须先删除原有的元素，再插入新的元素



#### set / multiset默认构造
```
set<int> setInt;                   //一个存放int的set容器
set<float> setFloat;               //一个存放float的set容器
set<string> setString;             //一个存放string的set容器
multiset<int> mulsetInt;           //一个存放int的multi set容器
multi set<float> multisetFloat;    //一个存放float的multi set容器
multi set<string> multisetString;  //一个存放string的multi set容器
```


#### set元素排序
```
set<int> setInt;                 //默认升序方式：该容器是按升序方式排列元素。
set<int,less<int> >  setIntA;    //该容器是按升序方式排列元素。
set<int,greater<int>> setIntB;   //该容器是按降序方式排列元素。
```


#### set与迭代器
```
set.insert(int elem);  //在容器中插入元素
set.begin();           //返回容器中第一个数据的迭代器
set.end();             //返回容器中最后一个数据之后的迭代器
set.rbegin();          //返回容器中倒数第一个元素的迭代器
set.rend();            //返回容器中倒数最后一个元素的后面的迭代器
```

#### set的拷贝构造与赋值
```
set(const set &st);		          //拷贝构造函数
set& operator=(const set &st);	//重载等号操作符
set.swap(st);			            	//交换两个集合容器
```


#### set的大小
```
set.size();	  //返回容器中元素的数目
set.empty();  //判断容器是否为空
```


#### set的删除
```
set.clear();		            //清除所有元素
set.erase(/*迭代器*/ pos);	  //删除pos迭代器所指的元素，返回下一个元素的迭代器。
set.erase(/*迭代器*/ beg,/*迭代器*/ end);	  //删除区间[beg,end)的所有元素	，返回下一个元素的迭代器。
set.erase(int elem);       //删除容器中值为elem的元素。
```

#### set的查找
```
set.find(int elem);         // 查找elem元素，返回指向elem元素的迭代器。
set.count(int elem);        // 返回容器中值为elem的元素个数。对set来说，要么是0，要么是1。对multiset来说，值可能大于1。
set.lower_bound(int elem);  // 返回第一个 >= elem元素的迭代器。
set.upper_bound(int elem);	// 返回第一个 > elem元素的迭代器。
set.equal_range(int elem);  // 返回容器中与elem相等的上下限的两个迭代器。上限是闭区间，下限是开区间，如[beg,end)。
                            // 以上函数返回两个迭代器，而这两个迭代器被封装在pair中。
```
